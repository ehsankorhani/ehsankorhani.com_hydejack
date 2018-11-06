---
layout: post
title: "ASP.NET MVC (weird) DropDownList"
date: 2016-12-05
---

Creating a dropdownlist in razor is kind of odd.

The general syntax is like this:

```csharp
@using (Html.BeginForm("Edit", "Robot", FormMethod.Post, new { id = "EditRobotForm", @class = "form-inline" }))
{
    ...
    <div class="form-group">

        <label for="RobotDdl" class="control-label left-label">Robot</label>

        @Html.DropDownListFor(model => model.RobotId, Model.Robots, new { id = "RobotDdl", @class = "form-control input-sm" })
    </div>

    ....
    <button type="button" id="btnSave" class="btn btn-primary btn-sm"><Save</button>
}
```
<!--more-->
in @Html.DropDownListFor:

* The first parameter is to set/get the selected value.
* The second parameter is to fill the dropdownlist.
* The third parameter is to add HTML attributes to the control tag (here i assumed that we are using twitter bootstrap).

The HTML output for the code above would be something like:

```html
<select class="form-control input-sm valid" id="RobotDdl" name="RobotId" aria-invalid="false">
    <option>--All--</option>
    <option selected="selected" value="1">Wall-E</option>
    <option value="2">R2D2</option>
    <option value="3">ASIMO</option>
</select>
```

Note that “Wall-E” is the selected item because in the controller we have had something like:

```csharp
model.RobotId = 1;
```

In addition, the “Model” itself should be of type List.

```csharp
public class RobotViewModel
{
    public string RobotId { get; set; }
    public List<SelectListItem> Robots { get; set; }
    ...
}
```

If you use **List**, then the default properties for data are (With the first letter in upper case even in JavaScript):
* Value
* Text
* Selected

Later I will demonstrate an alternative method to have more control over properties.

The odd thing about the output it HTML is that the is not updating to new option when you change the selected item. But you should not bother.

In this scenario, if you use Form Submit command (button type = Submit), the form will be posted to designated Action/Controller and your model.RobotId should be updated to the new robot. Although, you still can use JavaScript/jQuery to perform some action before submit (or even cancel submit).

```javascript
$(document).ready(function () {
    $("#EditRobotForm").submit(function (e) {
        // some validations
        if (validateForm() === false) {
            e.preventDefault();
            return false;  
        }
    });
});
```

The above approach is good when you want to leverage the power of C# model attributes (which will be reflected to HTML control creation by MVC) and JavaScript at the same time.

```csharp
public class RobotViewModel
{
    [Required]
    [Display(Name = "Robot")]
    public string RobotId { get; set; }
}
```

However, sometimes I like to go full JavaScript/jQuery when posting back data to the server (for example. in Partial Views).
In this case, I wouldn\’t specify the form button as a “submit”, but it will be just a normal “button”. And in the JS code we just write a listener for it.

```javascript
$(document).ready(function () {
    // ...
    $("#Container").on("click", "#btnSave", onSave);
    // ...
    var onSave = function (e) {
        $.post("/Automotive/Home/UpdateUserPreferredLocation", data)
            .done(done)
            .fail(fail);
    }
});
```

Note that all the above code should go into the corresponding App, Controller and Service modules. I also have removed all the complexities and this is just the bare bone of should have been done which is very convenient.

### More sophisticated model for dropdown

As I mentioned earlier you can define your own type of “SelectListItem” to gain more control over it. So we can have:

```csharp
[JsonObject(MemberSerialization.OptIn)]
public class RobotItemViewModel
{
    [JsonProperty(PropertyName = "id")]
    public string Id { get; set; }
    [JsonProperty(PropertyName = "name")]
    public string Name { get; set; }
}
```

And then use this in replacement for previous c# model definition code:

```csharp
public class RobotViewModel
{
    public string RobotId { get; set; }
    public List<RobotItemViewModel> Robots { get; set; }
    ...
}
```
