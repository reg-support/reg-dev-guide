# Coupon Check API

- The coupon check API validates a coupon code during checkout, and assuming the code is valid, returns a set of data related to the coupon.
- It is important to note that the server does not handle the actual calcuation of the updated price, so it is up to the client-side code to use the returned data to adjust the price before submitting.
- Another important note is that the server will not return any data for an invalid coupon code--it simply gives us a `404` error.
- The URL for this API is not provided in any other API results, but rather rendered via Liquid through the `coupon_check_url` variable.
  - (In ThemeNG, we have this embedded into a hidden element in `_homemaster.liquid`, so it can be accessed through DOM id `#coupon_check_url`.)

##### Coupon Types

- Coupon codes can be one of two types:
  - `fixed` - deducts a static amount from the original price
  - `percentage` - deducts a certain percentage from the original price
- Thus, the final price to be submitted can be calculated using something similar to the following pseudo-JS:

```javascript
if (coupon.type === 'fixed') {
  discount = coupon.value;
} else if (coupon.type === 'percentage') {
  discount = originalPrice * coupon.value;
}
discountedTotal = (originalPrice - discount).toFixed(2);
```

##### Returned Data

  - `_links [object]`
  - `code [string]`: the coupon code in use
  - `type [string]`: the coupon type; either `fixed` or `percentage`
  - `value [number]`: the static value of the coupon (i.e. unrelated to the price of the current event)
  - `value_display [number]`: the value formatted for currency
