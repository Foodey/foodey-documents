## Class Information

Here is the detail information for class diagram for the project.

- 💻 [List Of Class](#list-of-class)
- 👀 [Class Details](#class-details)
- 📁 [Back To Class Diagram](./only-classname.png)

## List Of Class

| Name                                    | Description |
| :-------------------------------------- | :---------- |
| [RegisterUser](#registeruser)           |             |
| [Foodeist](#foodeist)                   |             |
| [ShopOwner](#shopowner)                 |             |
| [Admin](#admin)                         |             |
| [Shipper](#shipper)                     |             |
| [Order](#order)                         |             |
| [OrderDetail](#orderdetail)             |             |
| [Discount](#discount)                   |             |
| [DiscountCondition](#discountcondition) |             |
| [Payment](#payment)                     |             |
| [Cash](#cash)                           |             |
| [ShoppingCart](#shoppingcart)           |             |
| [Product](#product)                     |             |
| [Store](#store)                         |             |
| [Menu](#menu)                           |             |

## Class Details

**NOTE**:

- Every class has a `created_at` and `updated_at` field with type is
  `DateTime` to manage the time of the object.
- Each property of the class has a `get` and `set` method to get and set the
  value of the property.

#### RegisterUser

| Element            |  Access   |   Type   | Unique  | Notes                                               | Description                  |
| :----------------- | :-------: | :------: | :-----: | :-------------------------------------------------- | :--------------------------- |
| `phoneNumber`      | `private` | `string` | `true`  | Value must be 10 digits                             | The phone with username role |
| `email`            | `private` | `string` | `true`  |                                                     |                              |
| `password`         | `private` | `string` | `false` | Value more than 8 characters                        |                              |
| `status`           | `private` |  `int`   | `false` | Value must be `1: alive`, `2: deleted`, `3: locked` |                              |
| `name`             | `private` | `string` | `false` |                                                     |                              |
| `avatar`           | `private` | `string` | `false` |                                                     |                              |
| `verify()`         | `public`  |  `bool`  | `false` |                                                     |                              |
| `login()`          | `public`  |  `bool`  | `false` |                                                     |                              |
| `logout()`         | `public`  |  `bool`  | `false` |                                                     |                              |
| `register()`       | `public`  |  `bool`  | `false` |                                                     |                              |
| `changePassword()` | `public`  |  `bool`  | `false` |                                                     |                              |
| `forgotPassword()` | `public`  |  `bool`  | `false` |                                                     |                              |

#### Foodeist

`NOTE` : `Foodeist` is inherited from `RegisterUser` class.

| Element   |  Access   |   Type   | Unique  | Notes | Description |
| :-------- | :-------: | :------: | :-----: | :---- | :---------- |
| `address` | `private` | `string` | `false` |       |             |

#### ShopOwner

`NOTE` : `ShopOwner` is inherited from `RegisterUser` class.

| Element | Access | Type | Unique | Notes | Description |
| :------ | :----: | :--: | :----: | :---- | :---------- |

#### Admin

`NOTE` : `Admin` is inherited from `RegisterUser` class.

| Element | Access | Type | Unique | Notes | Description |
| :------ | :----: | :--: | :----: | :---- | :---------- |

#### Shipper

`NOTE` : `Shipper` is inherited from `RegisterUser` class.

| Element           |  Access   |   Type   | Unique  | Notes                                         | Description |
| :---------------- | :-------: | :------: | :-----: | :-------------------------------------------- | :---------- |
| `rating`          | `private` |  `int`   | `false` | Value between 1-5 star                        |             |
| `vehicle`         | `private` |  `int`   | `false` | Value must be `1: Bike`, `2: Car`, `3: Truck` |             |
| `currentLocation` | `private` | `string` | `false` |                                               |             |
| `receiveOrder()`  | `public`  |  `bool`  | `false` |                                               |             |
| `shipOrder()`     | `public`  |  `bool`  | `false` |                                               |             |

#### Order

| Element        |  Access   |             Type              | Unique  | Notes                                                                                          | Description |
| :------------- | :-------: | :---------------------------: | :-----: | :--------------------------------------------------------------------------------------------- | :---------- |
| `id`           | `private` |           `string`            | `true`  |                                                                                                |             |
| `foodeist`     | `private` |    [`Foodeist`](#foodeist)    | `false` |                                                                                                |             |
| `store`        | `private` |       [`Store`](#store)       | `false` |                                                                                                |             |
| `shipper`      | `private` |     [`Shipper`](#shipper)     | `false` |                                                                                                |             |
| `status`       | `private` |             `int`             | `false` | The value must be `1: Waiting`, `2: Received`, `3: Preparing`, `4: Delivering`, `5: Completed` |             |
| `detail`       | `private` | [`OrderDetail`](#orderdetail) | `false` |                                                                                                |             |
| `create()`     | `public`  |            `bool`             | `false` |                                                                                                |             |
| `cancel()`     | `public`  |            `bool`             | `false` |                                                                                                |             |
| `pay()`        | `public`  |            `bool`             | `false` |                                                                                                |             |
| `ship()`       | `public`  |            `bool`             | `false` |                                                                                                |             |
| `receive()`    | `public`  |            `bool`             | `false` |                                                                                                |             |
| `viewDetail()` | `public`  |           `string`            | `false` |                                                                                                |             |

##### OrderDetail

| Element        |  Access   |               Type               | Unique  | Notes | Description |
| :------------- | :-------: | :------------------------------: | :-----: | :---- | :---------- |
| `id`           | `private` |             `string`             | `true`  |       |             |
| `products`     | `private` | `array<`[`Product`](#product)`>` | `false` |       |             |
| `discount`     | `private` |     [`Discount`](#discount)      | `false` |       |             |
| `payment`      | `private` |      [`Payment`](#payment)       | `false` |       |             |
| `address`      | `private` |             `string`             | `false` |       |             |
| `totalPrice()` | `public`  |              `int`               | `false` |       |             |

##### Discount

| Element        |  Access   |   Type   | Unique  | Notes | Description |
| :------------- | :-------: | :------: | :-----: | :---- | :---------- |
| `id`           | `private` | `string` | `true`  |       |             |
| `value`        | `private` |  `int`   | `false` |       |             |
| `type`         | `private` | `string` | `false` |       |             |
| `apply()`      | `public`  |  `bool`  | `false` |       |             |
| `checkValid()` | `public`  |  `bool`  | `false` |       |             |

##### DiscountDetail

| Element    |  Access   | Type  | Unique  | Notes | Description |
| :--------- | :-------: | :---: | :-----: | :---- | :---------- |
| `id`       | `private` | `int` | `true`  |       |             |
| `minPrice` | `private` | `int` | `false` |       |             |
| `minItem`  | `private` | `int` | `false` |       |             |

##### Payment

| Element  |  Access   |   Type   | Unique  | Notes                                | Description |
| :------- | :-------: | :------: | :-----: | :----------------------------------- | :---------- |
| `id`     | `private` |  `int`   | `true`  |                                      |             |
| `method` | `private` | `string` | `false` |                                      |             |
| `status` | `private` |  `bool`  | `false` | true for paid and false for not paid |             |
| `pay()`  | `public`  |  `bool`  | `false` |                                      |             |

##### ShoppingCart

| Element            |  Access   |               Type               | Unique  | Notes | Description |
| :----------------- | :-------: | :------------------------------: | :-----: | :---- | :---------- |
| `products`         | `private` | `array<`[`Product`](#product)`>` | `false` |       |             |
| `getTotalPrice()`  | `public`  |              `int`               | `false` |       |             |
| `checkout()`       | `public`  |              `bool`              | `false` |       |             |
| `updateQuantity()` | `public`  |              `bool`              | `false` |       |             |

##### Product

| Element       |  Access   |   Type   | Unique  | Notes | Description |
| :------------ | :-------: | :------: | :-----: | :---- | :---------- |
| `id`          | `private` |  `int`   | `true`  |       |             |
| `name`        | `private` | `string` | `false` |       |             |
| `price`       | `private` |  `int`   | `false` |       |             |
| `image`       | `private` | `string` | `false` |       |             |
| `description` | `private` | `string` | `false` |       |             |
| `category`    | `private` | `string` | `false` |       |             |
| `buy()`       | `public`  |  `bool`  | `false` |       |             |
| `sell()`      | `public`  |  `bool`  | `false` |       |             |
| `getDetail()` | `public`  | `string` | `false` |       |             |
| `addToCart()` | `public`  |  `bool`  | `false` |       |             |

##### Store

| Element           |  Access   |             Type             | Unique  | Notes | Description |
| :---------------- | :-------: | :--------------------------: | :-----: | :---- | :---------- |
| `id`              | `private` |            `int`             | `true`  |       |             |
| `name`            | `private` |           `string`           | `false` |       |             |
| `menu`            | `private` |       [`Menu`](#menu)        | `false` |       |             |
| `stores`          | `private` | `array<`[`Store`](#store)`>` | `false` |       |             |
| `viewRetailers()` | `public`  | `array<`[`Store`](#store)`>` | `false` |       |             |

##### Menu

| Element            |  Access   |               Type               | Unique  | Notes | Description |
| :----------------- | :-------: | :------------------------------: | :-----: | :---- | :---------- |
| `id`               | `private` |              `int`               | `true`  |       |             |
| `products`         | `private` | `array<`[`Product`](#product)`>` | `false` |       |             |
| `addProduct()`     | `public`  |              `bool`              | `false` |       |             |
| `removeProduct()`  | `public`  |              `bool`              | `false` |       |             |
| `searchProducts()` | `public`  | `array<`[`Product`](#product)`>` | `false` |       |             |
