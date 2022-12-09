# Drifting ruby - #277 - Diving into Hotwire
- https://www.driftingruby.com/episodes/diving-into-hotwire

- rails g scaffold products title "price:decimal{8,2}" 
- update product.rb

```
validates :title, presence: true, uniqueness: true
```

- routes

```
  root to: 'products#index'
```

- update layouts app

```

  <body>
    <div class="container">
      <%= link_to "Home", root_path %>
      <%= yield %>
    </div>

  </body>
```

- update the products new file

```
<%= turbo_frame_tag 'product' do %>
  <h1>New Product</h1>

  <%= render 'form', product: @product %>
  <%= link_to 'Back', products_path %>
<% end %>
```

- refresh the new products and try and submit
- it should refresh with out a re render
- update the show page

```
<%= turbo_frame_tag 'product' do %>
  <p style="color: green"><%= notice %></p>

  <%= render @product %>

  <div>
    <%= link_to "Edit this product", edit_product_path(@product) %> |
    <%= link_to "Back to products", products_path %>

    <%= button_to "Destroy this product", @product, method: :delete %>
  </div>
<% end %>
```

- update the edit products

```
<%= turbo_frame_tag 'product' do %>
  <h1>Editing product</h1>

  <%= render "form", product: @product %>

  <br>

  <div>
    <%= link_to "Show this product", @product %> |
    <%= link_to "Back to products", products_path %>
  </div>
<% end %>
```

- add around the products index as well

```
<%= turbo_frame_tag 'product' do %>
	.....
<% end %>
```

- refresh and click around, look at the address bar, it's always on localhost, none of the CRUD views

## THE END
