## Class Information

Here is the detail information for class diagram for the project.

- 💻 [List Of Class](#list-of-class)
- 👀 [Class Details](#class-details)
- 📁 [Back To Class Diagram](./only-classname.png)

## List Of Class

| Name                                    | Description                              |
| :-------------------------------------- | :--------------------------------------- |
| [Account](#account)                     | Account class                            |
| [Person](#person)                       | Person class                             |
| [Admin](#admin)                         | Admin class                              |
| [Customer](#customer)                   | Customer class                           |
| [Shipper](#shipper)                     | Shipper class                            |
| [Address](#address)                     | Address class                            |
| [Order](#order)                         | Order class                              |
| [OrderDetail](#orderdetail)             | The detail for order                     |
| [Discount](#discount)                   | The discount for order                   |
| [DiscountCondition](#discountcondition) | The condition for discount to be applied |
| [Payment](#payment)                     | The payment for order                    |
| [ShoppingCart](#shoppingcart)           | The shopping cart for customer           |
| [Product](#product)                     | Product class                            |
| [Store](#store)                         | Store class                              |
| [Menu](#menu)                           | The product menu of the store            |

## Class Details

**NOTE**:

- Every class has a `created_at` and `updated_at` field with type is
  `DateTime` to manage the time of the object.
- Each property of the class has a `get` and `set` method to get and set the
  value of the property.

##### Account

| Element              |  Access   |   Type   | Unique  | Notes                                               | Description                 |
| :------------------- | :-------: | :------: | :-----: | :-------------------------------------------------- | :-------------------------- |
| **email**            | `private` | `string` | `true`  | Value must be a valid email                         | The email of the account    |
| **password**         | `private` | `string` | `false` | Value more than 8 characters                        | The password of the account |
| **status**           | `private` |  `int`   | `false` | Value must be `1: alive`, `2: deleted`, `3: locked` | The status of the account   |
| **verify()**         | `public`  |  `bool`  | `false` |                                                     | Verify the account          |
| **login()**          | `public`  |  `bool`  | `false` |                                                     | Login the account           |
| **logout()**         | `public`  |  `bool`  | `false` |                                                     | Logout the account          |
| **register()**       | `public`  |  `bool`  | `false` |                                                     | Register the account        |
| **changePassword()** | `public`  |  `bool`  | `false` |                                                     | Change the password         |
| **forgotPassword()** | `public`  |  `bool`  | `false` |                                                     | Forgot the password         |

##### Person

| Element         |  Access   |         Type          | Unique  | Notes | Description |
| :-------------- | :-------: | :-------------------: | :-----: | :---- | :---------- |
| **name**        | `private` |       `string`        | `false` |       |             |
| **avatar**      | `private` |       `string`        | `false` |       |             |
| **phoneNumber** | `private` |       `string`        | `false` |       |             |
| **address**     | `private` | [`Address`](#address) | `false` |       |             |

##### Customer

Inherit from [`Person`](#person)

| Element |  Access   | Type  | Unique | Notes | Description |
| :------ | :-------: | :---: | :----: | :---- | :---------- |
| **id**  | `private` | `int` | `true` |       |             |

##### Shipper

Inherit from [`Person`](#person)

| Element          |  Access   |         Type          | Unique  | Notes | Description                        |
| :--------------- | :-------: | :-------------------: | :-----: | :---- | :--------------------------------- |
| **id**           | `private` |         `int`         | `true`  |       |                                    |
| **vehicle**      | `private` |       `string`        | `false` |       | The vehicle of the shipper to work |
| **activityArea** | `private` | [`Address`](#address) | `false` |       | The area for shipper to work       |

##### Address

| Element      | Access    | Type             | Unique  | Notes | Description |
| :----------- | :-------- | :--------------- | :------ | :---- | :---------- |
| **id**       | `private` | `int`            | `true`  |       |             |
| **city**     | `private` | `string`         | `false` |       |             |
| **district** | `private` | `string`         | `false` |       |             |
| **street**   | `private` | `string`         | `false` |       |             |
| **houseNo**  | `private` | `string` or `""` | `false` |       |             |

##### Order

| Element          |  Access   |             Type              | Unique  | Notes | Description |
| :--------------- | :-------: | :---------------------------: | :-----: | :---- | :---------- |
| **id**           | `private` |             `int`             | `true`  |       |             |
| **account**      | `private` |     [`Account`](#account)     | `false` |       |             |
| **store**        | `private` |       [`Store`](#store)       | `false` |       |             |
| **shipper**      | `private` |     [`Shipper`](#shipper)     | `false` |       |             |
| **status**       | `private` |           `string`            | `false` |       |             |
| **detail**       | `private` | [`OrderDetail`](#orderdetail) | `false` |       |             |
| **create()**     | `public`  |            `bool`             | `false` |       |             |
| **cancel()**     | `public`  |            `bool`             | `false` |       |             |
| **pay()**        | `public`  |            `bool`             | `false` |       |             |
| **ship()**       | `public`  |            `bool`             | `false` |       |             |
| **receive()**    | `public`  |            `bool`             | `false` |       |             |
| **showDetail()** | `public`  |           `string`            | `false` |       |             |

##### OrderDetail

| Element        |  Access   |               Type               | Unique  | Notes | Description |
| :------------- | :-------: | :------------------------------: | :-----: | :---- | :---------- |
| **id**         | `private` |              `int`               | `true`  |       |             |
| **products**   | `private` | `array<`[`Product`](#product)`>` | `false` |       |             |
| **totalPrice** | `private` |              `int`               | `false` |       |             |
| **discount**   | `private` |     [`Discount`](#discount)      | `false` |       |             |
| **payment**    | `private` |      [`Payment`](#payment)       | `false` |       |             |

##### Discount

| Element          |  Access   |                   Type                    | Unique  | Notes | Description |
| :--------------- | :-------: | :---------------------------------------: | :-----: | :---- | :---------- |
| **id**           | `private` |                   `int`                   | `true`  |       |             |
| **code**         | `private` |                 `string`                  | `true`  |       |             |
| **value**        | `private` |                   `int`                   | `false` |       |             |
| **type**         | `private` |                 `string`                  | `false` |       |             |
| **condition**    | `private` | [`DiscountCondition`](#discountcondition) | `false` |       |             |
| **due**          | `private` |                 `string`                  | `false` |       |             |
| **apply()**      | `public`  |                  `bool`                   | `false` |       |             |
| **checkValid()** | `public`  |                  `bool`                   | `false` |       |             |

##### DiscountCondition

| Element      |  Access   | Type  | Unique  | Notes | Description |
| :----------- | :-------: | :---: | :-----: | :---- | :---------- |
| **id**       | `private` | `int` | `true`  |       |             |
| **minPrice** | `private` | `int` | `false` |       |             |
| **minItem**  | `private` | `int` | `false` |       |             |

##### Payment

| Element    |  Access   |   Type   | Unique  | Notes | Description |
| :--------- | :-------: | :------: | :-----: | :---- | :---------- |
| **id**     | `private` |  `int`   | `true`  |       |             |
| **method** | `private` | `string` | `false` |       |             |

##### ShoppingCart

| Element              |  Access   |               Type               | Unique  | Notes | Description |
| :------------------- | :-------: | :------------------------------: | :-----: | :---- | :---------- |
| **products**         | `private` | `array<`[`Product`](#product)`>` | `false` |       |             |
| **getTotalPrice()**  | `public`  |              `int`               | `false` |       |             |
| **checkout()**       | `public`  |              `bool`              | `false` |       |             |
| **updateQuantity()** | `public`  |              `bool`              | `false` |       |             |

##### Product

| Element         |  Access   |   Type   | Unique  | Notes | Description                   |
| :-------------- | :-------: | :------: | :-----: | :---- | :---------------------------- |
| **id**          | `private` |  `int`   | `true`  |       |                               |
| **name**        | `private` | `string` | `false` |       | The name of the product       |
| **price**       | `private` |  `int`   | `false` |       | The price of the product      |
| **image**       | `private` | `string` | `false` |       | The image of the product      |
| **buy()**       | `public`  |  `bool`  | `false` |       | Buy the product               |
| **sell()**      | `public`  |  `bool`  | `false` |       | Sell the product              |
| **getDetail()** | `public`  | `string` | `false` |       | Get the detail of the product |
| **addToCart()** | `public`  |  `bool`  | `false` |       | Add the product to cart       |

##### Store

| Element             |  Access   |             Type             | Unique  | Notes | Description |
| :------------------ | :-------: | :--------------------------: | :-----: | :---- | :---------- |
| **id**              | `private` |            `int`             | `true`  |       |             |
| **name**            | `private` |           `string`           | `false` |       |             |
| **menu**            | `private` |       [`Menu`](#menu)        | `false` |       |             |
| **stores**          | `private` | `array<`[`Store`](#store)`>` | `false` |       |             |
| **viewRetailers()** | `public`  | `array<`[`Store`](#store)`>` | `false` |       |             |

##### Menu

| Element              |  Access   |               Type               | Unique  | Notes | Description |
| :------------------- | :-------: | :------------------------------: | :-----: | :---- | :---------- |
| **id**               | `private` |              `int`               | `true`  |       |             |
| **products**         | `private` | `array<`[`Product`](#product)`>` | `false` |       |             |
| **addProduct()**     | `public`  |              `bool`              | `false` |       |             |
| **removeProduct()**  | `public`  |              `bool`              | `false` |       |             |
| **searchProducts()** | `public`  | `array<`[`Product`](#product)`>` | `false` |       |             |
