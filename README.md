# How to attach an image with Rails Active Storage
This guide makes use of a generated scaffold

## Setup
Within the project: 
1. run `rails active_storage:isntall`
2. run `rails db:migrate`
3. add `has_one_attached :image` to model that will have image attached  
  note: The symbol `:image` can be changed to anything

## Permit the image within the controller
Go to the model controller, and add `:image` to the permit method. For example:
`
def car_params
  params.require(:car).permit(:brand, :model, :image)
end
`

## Add image field to a form
This example will make use of the `form_with` form helper

Include `form.file_field :image` in the view:  
```
<div class="field">
  <%= form.label :image %>
  <%= form.field_field :image %>
</div>
```  
  note: `:image` is the name of the symbol attached within the model (from Setup: step 3). If the name in the model is different, use that within the view
  
## Display the image
Add `<%= image_tag(@car.image) %>` to the view
  note: `image` is the name of the symbol attached within the model
