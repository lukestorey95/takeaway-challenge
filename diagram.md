# Diagram

```
Takeaway
  @menu Menu
  @current_order Order
  
  view_menu
    should return Menu

  add_to_order(items)
    should create a new Order

  when at least one item is provided
    when all the items match dishes on the Menu
      should change current_order selected_items by at least 1

    when not all the items match dishes on the Menu
      should raise error

  when no items are not provided
    should raise error

  place_order
    when current_order and selected_items are not empty
      should change current_order order_complete from false to true
      should instruct Text to send_text
    
    when current_order selected_items are empty
      should raise error

Order
  @selected_items []
  @order_total_price 0.00
  @order_complete false
  @order_placed_time Time

  check_order_total_matches_item_total
    when selected_items are not empty
      should return list of selected_items, prices and order_total_price

    when selected_items are empty
      should raise error

Menu
  @dishes_menu [{ name: “”, price: 0.00, available: true}]

  display_available_dishes
    when dishes_menu contains available dishes
      should return list of available dishes names and prices 

    when dishes_menu is empty
      should raise error

  import_dishes
    when dishes are not empty
      should change dishes_menu by at least 1

    when dishes are empty
      should raise error

Text
  ORDER_CONFIRMATION_MESSAGE

  @client Twilio::REST::Client
  @message_body “”

  send_text
    should instruct client with message_body and order_placed_time
```