## Class Information

Here is the detail information for class diagram for the project.

- 💻 [List Of Class](#list-of-class)
- 👀 [Detail Of Class, Interface, Enum](#detail-of-class-interface-enum)
- 📁 [Back To Class Diagram](./only-classname.png)

## List Of Class, Interface, Enum

#### 2. Class

| Name                                    | Description                                                                                                                                                                                                                                        |
| :-------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Account](#account)                     |                                                                                                                                                                                                                                                    |
| [Customer](#customer)                   | The abstract class of FoodeyGuest and FoodeMember                                                                                                                                                                                                  |
| [FoodeyGuest](#foodeyguest)             | Unregistered account customer                                                                                                                                                                                                                      |
| [FoodeyMember](#foodeymember)           | Registered account customer                                                                                                                                                                                                                        |
| [SystemAdmin](#systemadmin)             |                                                                                                                                                                                                                                                    |
| [Shipper](#shipper)                     |                                                                                                                                                                                                                                                    |
| [ShopOwner](#shopowner)                 |                                                                                                                                                                                                                                                    |
| [ShoppingCart](#shoppingcart)           | Users will add product items that they intend to buy to the shopping cart                                                                                                                                                                          |
| [ShopMenu](#shopmenu)                   |                                                                                                                                                                                                                                                    |
| [Shop](#shop)                           |                                                                                                                                                                                                                                                    |
| [Order](#order)                         | This will encapsulate a buying order to buy everything in the shopping cart                                                                                                                                                                        |
| [OrderLog](#orderlog)                   | Will keep a track of the status of orders, such as unshipped, pending, complete, canceled, etc.                                                                                                                                                    |
| [OrderItem](#orderitem)                 | This class will encapsulate a product item that the users will be buying or placing in the shopping cart. For example, a pen could be a product and if there are 10 pens in the inventory, each of these 10 pens will be considered a product item |
| [Bill](#bill)                           | Encapsulate the entity of the bill                                                                                                                                                                                                                 |
| [Product](#product)                     | This class will encapsulate the entity that the users of our system will be buying and selling. Each Product will belong to a ProductCategory                                                                                                      |
| [ProductCategory](#productcategory)     | This will encapsulate the different categories of products, such as books, electronics, etc                                                                                                                                                        |
| [Review](#review)                       | The abstract class of ShopReview and ShipperReview                                                                                                                                                                                                 |
| [ShopReview](#shopreview)               | Any registered member can add a review about a shop                                                                                                                                                                                                |
| [ShipperReview](#productreview)         | Any registered member can add a review about a shipper                                                                                                                                                                                             |
| [Catalog](#catalog)                     | Users of our system can search for products by their name or category and shop by their name. This class will keep an index of all products for faster search                                                                                      |
| [Notification](#notification)           | This class will take care of sending notifications to customers                                                                                                                                                                                    |
| [SMSNotification](#smsnotification)     | This class will take care of sending notifications to customers by SMS                                                                                                                                                                             |
| [EmailNotification](#emailnotification) | This class will take care of sending notifications to customers by Email                                                                                                                                                                           |
| [Payment](#payment)                     | This class will encapsulate the payment for an order. Members can pay through credit card(not now) or cash                                                                                                                                         |

#### 2. Interface

| Name                | Description                                 |
| :------------------ | :------------------------------------------ |
| [ISearch](#isearch) | The interface for all the search activities |

#### 3. Enum

| Name                            | Description           |
| :------------------------------ | :-------------------- |
| [AccountStatus](#accountstatus) | The status of Account |
| [OrderStatus](#orderstatus)     | The status of order   |
| [ShipperStatus](#shipperstatus) | The status of shipper |
| [PaymentStatus](#paymentstatus) | The status of payment |

## Detail Of Class, Interface, Enum

#### 1. Class

##### Account

| Element                |  Access   |               Type                | Unique  | Notes                             | Description                |
| :--------------------- | :-------: | :-------------------------------: | :-----: | :-------------------------------- | :------------------------- |
| `phone`                | `private` |             `string`              | `true`  | Value must be a valid email       | Plays the role of username |
| `password`             | `private` |             `string`              | `false` | Value more than 8 characters      |                            |
| `name`                 | `private` |             `string`              | `false` | Value more than 8 characters      |                            |
| `avatar`               | `private` |             `string`              | `false` |                                   |                            |
| `status`               | `private` | [`AccountStatus`](#accountstatus) | `false` | Default is `AccountStatus.Active` |                            |
| `shipping_address`     | `private` |             `string`              | `false` | Value more than 8 characters      |                            |
| `getShippingAddress()` | `public`  |             `string`              | `false` |                                   |                            |

##### Customer

| Element                |  Access  |                 Type                 | Unique | Notes | Description |
| :--------------------- | :------: | :----------------------------------: | :----: | :---- | :---------- |
| `getShoppingCart()`    | `public` | `array<`[`OrderItem`](#orderitem)`>` |        |       |             |
| `addItemToCart()`      | `public` |                `bool`                |        |       |             |
| `removeItemFromCart()` | `public` |                `bool`                |        |       |             |

##### FoodeyGuest

**NOTE**: Inherit from [`Customer`](#customer) class.

| Element             |  Access  |  Type  | Unique  | Notes | Description |
| :------------------ | :------: | :----: | :-----: | :---- | :---------- |
| `registerAccount()` | `public` | `void` | `false` |       |             |

##### FoodeyMember

**NOTE**: Inherit from [`Customer`](#customer) class.

| Element                   |  Access   |               Type                | Unique  | Notes | Description                       |
| :------------------------ | :-------: | :-------------------------------: | :-----: | :---- | :-------------------------------- |
| `orders`                  | `private` |   `array<`[`Order`](#order)`>`    | `false` |       |                                   |
| `account`                 | `private` |       [`Account`](#account)       | `false` |       |                                   |
| `order()`                 | `public`  |              `bool`               | `false` |       |                                   |
| `favoriteProductIds`      | `private` |          `array<string>`          | `false` |       |                                   |
| `getFavoriteProducts()`   | `public`  | `array<`[`Product`](#produuct)`>` | `false` |       |                                   |
| `addFavoriteProduct()`    | `public`  |              `bool`               | `false` |       |                                   |
| `getOldOrders()`          | `public`  |              `bool`               | `false` |       | Get completed orders              |
| `getNotDeliveredOrders()` | `public`  |              `bool`               | `false` |       | Get the not delivered list orders |
| `trackProfit()`           | `public`  |          `unsigned long`          | `false` |       |                                   |

##### SystemAdmin

| Element                   |  Access   |         Type          | Unique  | Notes | Description |
| :------------------------ | :-------: | :-------------------: | :-----: | :---- | :---------- |
| `account`                 | `private` | [`Account`](#account) | `false` |       |             |
| `addNewProductCategory()` | `public`  |        `bool`         | `false` |       |             |
| `modifyProductCategory()` | `public`  |        `bool`         | `false` |       |             |
| `approveNewShop()`        | `public`  |        `bool`         | `false` |       |             |
| `approveNewShipper()`     | `public`  |        `bool`         | `false` |       |             |
| `blockAccount()`          | `public`  |        `bool`         | `false` |       |             |

##### Shipper

| Element                                  |  Access   |               Type                | Unique  | Notes | Description                          |
| :--------------------------------------- | :-------: | :-------------------------------: | :-----: | :---- | :----------------------------------- |
| `identifyImages`                         | `private` |          `array<string>`          | `false` |       | 2 anh can cuoc cong dan (truoc, sau) |
| `motorbicycleLicenseImages`              | `private` |          `array<string>`          | `false` |       | 2 anh bang lai xe (truoc, sau)       |
| `motorbikeRegistrationCertificateImages` | `private` |          `array<string>`          | `false` |       | 2 anh giay dang ky xe (truoc, sau)   |
| `judicialResumeImage`                    | `private` |             `string`              | `false` |       | 1 anh giay to tien pham              |
| `account`                                | `private` |       [`Account`](#account)       | `false` |       |                                      |
| `status`                                 | `private` | [`ShipperStatus`](#shipperstatus) | `false` |       |                                      |
| `getCurrentLocation()`                   | `public`  |             `string`              | `false` |       |                                      |
| `getCurrentCustomerOrders()`             | `public`  |   `array<`[`Order`](#order)`>`    | `false` |       |                                      |
| `receiveOrder()`                         | `public`  |         [`Order`](#order)         | `false` |       |                                      |
| `declineOrder()`                         | `public`  |         [`Order`](#order)         | `false` |       |                                      |

##### ShopOwner

| Element          |  Access   |            Type            | Unique  | Notes | Description                          |
| :--------------- | :-------: | :------------------------: | :-----: | :---- | :----------------------------------- |
| `identifyImages` | `private` |      `array<string>`       | `false` |       | 2 anh can cuoc cong dan (truoc, sau) |
| `account`        | `private` |   [`Account`](#account)    | `false` |       |                                      |
| `getShops()`     | `public`  | `array<`[`Shop`](#shop)`>` | `false` |       |                                      |
| `registerShop()` | `public`  |          `boold`           | `false` |       |                                      |
| `updateShop()`   | `public`  |           `bool`           | `false` |       |                                      |
| `deleteShop()`   | `public`  |          `boold`           | `false` |       |                                      |
| `trackProfit()`  | `public`  |      `unsigned long`       | `false` |       |                                      |

##### ShoppingCart

| Element                |  Access   |                 Type                 | Unique  | Notes | Description |
| :--------------------- | :-------: | :----------------------------------: | :-----: | :---- | :---------- |
| `orderItems`           | `private` | `array<`[`OrderItem`](#orderitem)`>` | `false` |       |             |
| `getOrderItems()`      | `public`  | `array<`[`OrderItem`](#orderitem)`>` | `false` |       |             |
| `addItem()`            | `public`  |                `bool`                | `false` |       |             |
| `removeItem()`         | `public`  |                `bool`                | `false` |       |             |
| `updateItemQuantity()` | `public`  |                `bool`                | `false` |       |             |
| `getTotalPrice()`      | `public`  |           `unsigned long`            | `false` |       |             |
| `checkout()`           | `public`  |                `bool`                | `false` |       |             |
| `clear()`              | `public`  |                `bool`                | `false` |       |             |

##### Order

| Element                    |  Access   |                 Type                 | Unique  | Notes | Description |
| :------------------------- | :-------: | :----------------------------------: | :-----: | :---- | :---------- |
| `id`                       | `private` |           `unsigned long`            | `true`  |       |             |
| `shop`                     | `private` |           [`Shop`](#shop)            | `false` |       |             |
| `shipper`                  | `private` |        [`Shipper`](#shipper)         | `false` |       |             |
| `items`                    | `private` | `array<`[`OrderItem`](#orderitem)`>` | `false` |       |             |
| `status`                   | `private` |    [`OrderStatus`](#orderstatus)     | `false` |       |             |
| `createAt`                 | `private` |              `DateTime`              | `false` |       |             |
| `updateAt`                 | `private` |              `DateTime`              | `false` |       |             |
| `sendToShipper(shipperId)` | `public`  |              `DateTime`              | `false` |       |             |
| `printBill()`              | `public`  |                `bool`                | `false` |       |             |

##### OrderLog

| Element    |  Access   |             Type              | Unique  | Notes | Description |
| :--------- | :-------: | :---------------------------: | :-----: | :---- | :---------- |
| `createAt` | `private` |          `DateTime`           |         |       |             |
| `status`   | `private` | [`OrderStatus`](#orderstatus) | `false` |       |             |

##### Bill

| Element      |  Access   |                 Type                 | Unique  | Notes | Description |
| :----------- | :-------: | :----------------------------------: | :-----: | :---- | :---------- |
| `id`         | `private` |           `unsigned long`            | `true`  |       |             |
| `orderID`    | `private` |           `unsigned long`            | `false` |       |             |
| `orderDate`  | `private` |              `DateTime`              | `false` |       |             |
| `totalPrice` | `private` |           `unsigned long`            | `false` |       |             |
| `items`      | `private` | `array<`[`OrderItem`](#orderitem)`>` | `false` |       |             |
| `createAt`   | `private` |              `DateTime`              | `false` |       |             |
| `print()`    | `public`  |                `bool`                | `false` |       |             |

##### OrderItem

| Element     |  Access   |      Type       | Unique  | Notes | Description |
| :---------- | :-------: | :-------------: | :-----: | :---- | :---------- |
| `productId` | `private` | `unsigned long` | `true`  |       |             |
| `name`      | `private` |    `string`     | `false` |       |             |
| `price`     | `private` | `unsigned long` | `false` |       |             |
| `quantity`  | `private` |      `int`      | `false` |       |             |

##### Product

| Element                                                             |  Access   |                 Type                  | Unique | Notes | Description |
| :------------------------------------------------------------------ | :-------: | :-----------------------------------: | :----: | :---- | :---------- |
| `id`                                                                | `private` |            `unsigned long`            |        |       |             |
| `name`                                                              | `private` |               `string`                |        |       |             |
| `image`                                                             | `private` |               `string`                |        |       |             |
| `price`                                                             | `private` |               `string`                |        |       |             |
| `description`                                                       | `private` |               `string`                |        |       |             |
| `category`                                                          | `private` | [`ProductCategory`](#productcategory) |        |       |             |
| `inventoryQuantity`                                                 | `private` |                 `int`                 |        |       |             |
| `shopId`                                                            | `private` |            `unsigned long`            |        |       |             |
| `createAt`                                                          | `private` |              `DateTime`               |        |       |             |
| `updateAt`                                                          | `private` |              `DateTime`               |        |       |             |
| `getInventoryQuantity()`                                            | `public`  |                 `int`                 |        |       |             |
| `update([name,image,price,description,category,inventoryQuantity])` | `public`  |                `bool`                 |        |       |

##### ProductCategory

| Element       |  Access   |   Type   | Unique  | Notes | Description |
| :------------ | :-------: | :------: | :-----: | :---- | :---------- |
| `name`        | `private` | `string` | `true`  |       |             |
| `description` | `private` | `string` | `false` |       |             |

##### Shop

| Element    |  Access   |                Type                | Unique  | Notes | Description |
| :--------- | :-------: | :--------------------------------: | :-----: | :---- | :---------- |
| `name`     | `private` |              `string`              | `false` |       |             |
| `image`    | `private` |              `string`              | `false` |       |             |
| `address`  | `private` |              `string`              | `false` |       |             |
| `phone`    | `private` |              `string`              | `false` |       |             |
| `email`    | `private` |              `string`              | `false` |       |             |
| `menus`    | `private` | `array<`[`ShopMenu`](#shopmenu)`>` | `false` |       |             |
| `branches` | `private` |     `array<`[`Shop`](#shop)`>`     | `false` |       |

##### ShopMenu

| Element       |  Access   |               Type               | Unique  | Notes | Description |
| :------------ | :-------: | :------------------------------: | :-----: | :---- | :---------- |
| `name`        | `private` |             `string`             | `false` |       |             |
| `description` | `private` |             `string`             | `false` |       |             |
| `products`    | `private` | `array<`[`Product`](#product)`>` | `false` |       |             |

<!-- ------------------------ Interface -------------------------->

##### Review

| Element       |  Access   |         Type          | Unique  | Notes | Description |
| :------------ | :-------: | :-------------------: | :-----: | :---- | :---------- |
| `reviewer`    | `private` | [`Account`](#account) | `false` |       |             |
| `content`     | `private` |       `string`        | `false` |       |             |
| `rating`      | `private` |        `float`        | `false` |       |             |
| `createAt`    | `private` |      `DateTime`       | `false` |       |             |
| `updateAt`    | `private` |      `DateTime`       | `false` |       |             |
| `getRating()` | `public`  |        `float`        | `false` |       |             |

##### ShopReview

**NOTE**: Inherit from [`Review`](#review) class.

| Element  |  Access   |      Type       | Unique  | Notes | Description |
| :------- | :-------: | :-------------: | :-----: | :---- | :---------- |
| `shopId` | `private` | `unsigned long` | `false` |       |             |

##### ShipperReview

**NOTE**: Inherit from [`Review`](#review) class.

| Element     |  Access   |      Type       | Unique  | Notes | Description |
| :---------- | :-------: | :-------------: | :-----: | :---- | :---------- |
| `shipperId` | `private` | `unsigned long` | `false` |       |             |

##### Catalog

| Element             |  Access   |                   Type                    | Unique  | Notes | Description |
| :------------------ | :-------: | :---------------------------------------: | :-----: | :---- | :---------- |
| `productNames`      | `private` | `HashMap<string,`[`Product`](#product)`>` | `false` |       |             |
| `productCategories` | `private` | `HashMap<string,`[`Product`](#product)`>` | `false` |       |             |
| `shopNames`         | `private` |    `HashMap<string,`[`Shop`](#shop)`>`    | `false` |       |             |

##### Notification

| Element    |  Access   |    Type    | Unique  | Notes | Description |
| :--------- | :-------: | :--------: | :-----: | :---- | :---------- |
| `id`       | `private` |  `string`  | `true`  |       |             |
| `createAt` | `private` | `DateTime` | `false` |       |             |
| `content`  | `private` |  `string`  | `false` |       |             |
| `send()`   | `public`  |   `bool`   | `false` |       |             |

##### SMSNotification

**NOTE**: Inherit from [`Notification`](#notification) class.

| Element |  Access   |   Type   | Unique  | Notes | Description |
| :------ | :-------: | :------: | :-----: | :---- | :---------- |
| `phone` | `private` | `string` | `false` |       |             |

##### EmailNotification

**NOTE**: Inherit from [`Notification`](#notification) class.

| Element |  Access   |   Type   | Unique  | Notes | Description |
| :------ | :-------: | :------: | :-----: | :---- | :---------- |
| `email` | `private` | `string` | `false` |       |             |

#### 2. Interface

##### ISearch

| Element                      |  Access  |                Type                | Notes | Description |
| :--------------------------- | :------: | :--------------------------------: | :---- | ----------- |
| `searchProductsByName()`     | `public` | `array<`[`Products`](#product)`>`  |       |             |
| `searchProductsByCatagory()` | `public` | `array<`[`Category`](#category)`>` |       |             |
| `searchShopsByName()`        | `public` |     `array<`[`Shop`](#shop)`>`     |       |             |

<!-- ------------------------ Enum -------------------------->

#### 3. Enum

##### AccountStatus

| Element       | Description                                   |
| :------------ | :-------------------------------------------- |
| `Active`      | Status when account is using                  |
| `Blocked`     | Status when account is blocked                |
| `Banned`      | Status when account is banned by admin        |
| `Compromised` | Status when account is compromised by someone |
| `Archived`    | Status when account is deleted                |
| `Unknown`     |                                               |

##### OrderStatus

| Element           | Description                                                                                                                                   |
| :---------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- |
| `FoundingShipper` | Status after order meal and trying to find a shipper                                                                                          |
| `ShipperReceived` | Status after shipper receive order                                                                                                            |
| `NoShipperFound`  | Status after timeout(2 minitues) and no shipper receive that order                                                                            |
| `StoreConfirmed`  | Status after user has ordered meal and the store confirms it(After this status then the shipper can see the customer order to start delivery) |
| `Delivering`      | Status when the order is in delivering time                                                                                                   |
| `Delivered`       | Status after the customer receive the order from shipper                                                                                      |
| `Cancel`          | Status after cancel the order                                                                                                                 |
| `Unknown`         |                                                                                                                                               |

##### ShipperStatus

| Element      | Description                                                                |
| :----------- | :------------------------------------------------------------------------- |
| `Idle`       | The shipper can start deliver                                              |
| `Delivering` | The status between received order from customer to delivered itto customer |
| `Unknown`    |                                                                            |

##### PaymentStatus

| Element     | Description |
| :---------- | :---------- |
| `Unpaid`    |             |
| `Pending`   |             |
| `Completed` |             |
| `Failed`    |             |
| `Declined`  |             |
| `Canceled`  |             |
| `Abandoned` |             |
| `Setting`   |             |
| `Settled`   |             |
| `Refunded`  |             |