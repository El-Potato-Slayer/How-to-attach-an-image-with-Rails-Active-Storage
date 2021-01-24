# How to attach an image with Rails Active Storage
This guide makes use of a generated scaffold, where the model is `Car`, and makes use of a params controller method and a `form_with` form helper

## Setup
Within the project: 
1. run `rails active_storage:isntall`
2. run `rails db:migrate`
3. add `has_one_attached :image` to model that will have image attached  
  note: The symbol `:image` can be changed to anything you choose. Any other references of `:image` within this guide will be what it's named in the model.

## Permit the image within the controller

Go to the model controller, and add `:image` to the permit method. For example:
```
def car_params
  params.require(:car).permit(:brand, :model, :image)
end
```  

## Add image field to a form

Include `form.file_field :image` in the view:  
```
<div class="field">
  <%= form.label :image %>
  <%= form.file_field :image %>
</div>
```  
  
## Display the image
Add `<%= image_tag(@car.image) %>` to the view  
