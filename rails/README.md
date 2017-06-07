# Rails Style

## Routing & Controllers

#### Avoid `member` and `collection` routes

```Ruby
# Bad

resources :catering_orders do
  member do
    post :cancel
  end
end


# Good

resources :catering_orders do
  resource :cancellation, only: [:create]
end

# -or-

resources :catering_orders
resources :catering_order_cancellation, only: [:create]
```

##### Why?
* Prevents existing controllers from becoming too busy
* Eases the use of ember-data
* What were once simple concepts such as `cancel` or `accept` or `reject` usually grow to become substantial domain concepts of their own, meriting their own controller.
