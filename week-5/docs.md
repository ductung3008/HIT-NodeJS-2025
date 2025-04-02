# Buổi 5: MongoDB và Mongoose

## 1. [NoSQL](https://www.mongodb.com/en/resources/basics/databases/nosql-explained)

### 1.1. NoSQL là gì?

-   NoSQL (Not Only SQL) là mô hình cơ sở dữ liệu phi quan hệ, không sử dụng ngôn ngữ SQL để truy vấn dữ liệu.
-   NoSQL không tuân thủ theo mô hình quan hệ, không có schema cố định, không có các ràng buộc như khóa ngoại, không có các quy tắc chuẩn như ACID.
-   NoSQL thường được sử dụng trong các hệ thống lớn, cần xử lý lượng dữ liệu lớn, cần mở rộng dễ dàng.

### 1.2. Các loại NoSQL

-   Document Store: Lưu trữ dữ liệu dưới dạng document (JSON, XML, BSON).
-   Key-Value Store: Lưu trữ dữ liệu dưới dạng cặp key-value.
-   Wide-Column Store: Lưu trữ dữ liệu dưới dạng cột.
-   Graph Store: Lưu trữ dữ liệu dưới dạng đồ thị.

![NoSQL's types](https://learn.microsoft.com/en-us/dotnet/architecture/cloud-native/media/types-of-nosql-datastores.png)

### 1.3. Ưu và nhược điểm của NoSQL

#### Ưu điểm

-   Linh hoạt, dễ dàng mở rộng.
-   Hiệu suất cao, xử lý lượng dữ liệu lớn.
-   Phù hợp với các ứng dụng cần lưu trữ dữ liệu không cấu trúc.

#### Nhược điểm

-   Không hỗ trợ các tính năng quan hệ như JOIN, ACID.
-   Ít chuẩn hóa dữ liệu, dễ gây trùng lặp dữ liệu.

## 2. [MongoDB](https://www.mongodb.com/)

### 2.1. MongoDB là gì?

-   MongoDB là một hệ thống quản lý cơ sở dữ liệu NoSQL, lưu trữ dữ liệu dưới dạng document.
-   MongoDB không sử dụng ngôn ngữ SQL, thay vào đó sử dụng các phương thức truy vấn dữ liệu dựa trên JSON.

### 2.2. Cài đặt MongoDB

-   Cài đặt [MongoDB Community](https://www.mongodb.com/try/download/community).
-   Cài đặt [MongoDB Compass](https://www.mongodb.com/try/download/compass) để quản lý cơ sở dữ liệu.

## 3. [Mongoose](https://mongoosejs.com/)

### 3.1. ORM và ODM

#### ORM

-   ORM (Object-Relational Mapping) là một kỹ thuật để ánh xạ dữ liệu giữa cơ sở dữ liệu quan hệ và các đối tượng trong mã nguồn.
-   Cho phép thao tác với dữ liệu dễ dàng thông qua các đối tượng, không cần viết các câu truy vấn SQL.
-   Ví dụ: Sequelize, TypeORM.

#### ODM

-   ODM (Object-Document Mapping) là một kỹ thuật để ánh xạ dữ liệu giữa cơ sở dữ liệu NoSQL dạng document-based và các đối tượng trong mã nguồn.
-   Ví dụ: Mongoose.

### 3.2. [Mongoose](https://mongoosejs.com/) là gì?

-   Mongoose là một thư viện ODM giúp quản lý cơ sở dữ liệu MongoDB dễ dàng hơn.
-   Hỗ trợ schema validation, middleware, query linh hoạt, ...

### 3.3. Cài đặt Mongoose

```bash
npm install mongoose
```

### 3.4. Kết nối MongoDB với Mongoose

```js
const mongoose = require('mongoose');

mongoose
    .connect('mongodb://localhost:27017/your-database', {
        useNewUrlParser: true,
        useUnifiedTopology: true,
    })
    .then(() => console.log('Connected to MongoDB'))
    .catch((error) => console.error(error));
```

### 3.5. Tạo model với Mongoose

`src/models/user.model.js`

```js
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
    name: String,
    age: Number,
    email: String,
    password: String,
});

const User = mongoose.model('User', userSchema);

module.exports = User;
```

### 3.6. Thao tác với model

#### Thêm dữ liệu

```js
const User = require('./models/user.model');

const createUser = async (req, res) => {
    try {
        const user = await User.create(req.body);
        res.status(201).json(user);
    } catch (error) {
        res.status(500).json(error);
    }
};
```

#### Lấy dữ liệu

```js
const getUsers = async (req, res) => {
    try {
        const users = await User.find();
        res.status(200).json(users);
    } catch (error) {
        res.status(500).json(error);
    }
};
```

#### Sửa dữ liệu

```js
const updateUser = async (req, res) => {
    try {
        const user = await User.findById(req.params.id);
        Object.assign(user, req.body);
        await user.save();
    } catch (error) {
        res.status(500).json(error);
    }
};
```

#### Xóa dữ liệu

```js
const deleteUser = async (req, res) => {
    try {
        await User.findByIdAndDelete(req.params.id);
        res.status(204).end();
    } catch (error) {
        res.status(500).json(error);
    }
};
```
