# Buổi 9: Mối quan hệ giữa các Model. Truy vấn nâng cao

## 1. Mối quan hệ giữa các Model (MongoDB, Mongoose)

### 1.1 Mối quan hệ 1-1

-   Mối quan hệ 1-1 là mối quan hệ giữa hai bảng, trong đó mỗi bản ghi trong bảng này chỉ liên kết với một bản ghi duy nhất trong bảng kia.
-   Ví dụ: Một người dùng chỉ có một địa chỉ giao hàng duy nhất.
-   Để thiết lập mối quan hệ 1-1 trong Mongoose, bạn có thể sử dụng `ref` để tham chiếu đến model khác.

```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
    name: String,
    email: String,
    address: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Address',
    },
});

const addressSchema = new mongoose.Schema({
    street: String,
    city: String,
    state: String,
    zip: String,
});

const User = mongoose.model('User', userSchema);
const Address = mongoose.model('Address', addressSchema);
```

### 1.2 Mối quan hệ 1-n

-   Mối quan hệ 1-n là mối quan hệ giữa hai bảng, trong đó mỗi bản ghi trong bảng này có thể liên kết với nhiều bản ghi trong bảng kia.
-   Ví dụ: Một người dùng có thể có nhiều bài viết.
-   Để thiết lập mối quan hệ 1-n trong Mongoose, bạn có thể sử dụng `ref` để tham chiếu đến model khác.

```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
    name: String,
    email: String,
});

const postSchema = new mongoose.Schema({
    title: String,
    content: String,
    author: {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'User',
    },
});

const User = mongoose.model('User', userSchema);
const Post = mongoose.model('Post', postSchema);
```

### 1.3 Mối quan hệ n-n

-   Mối quan hệ n-n là mối quan hệ giữa hai bảng, trong đó mỗi bản ghi trong bảng này có thể liên kết với nhiều bản ghi trong bảng kia và ngược lại.
-   Ví dụ: Một bài viết có thể có nhiều thẻ và một thẻ có thể thuộc về nhiều bài viết.
-   Để thiết lập mối quan hệ n-n trong Mongoose, bạn có thể sử dụng `ref` để tham chiếu đến model khác và sử dụng mảng để lưu trữ nhiều giá trị.

```javascript
const mongoose = require('mongoose');

const postSchema = new mongoose.Schema({
    title: String,
    content: String,
    tags: [
        {
            type: mongoose.Schema.Types.ObjectId,
            ref: 'Tag',
        },
    ],
});

const tagSchema = new mongoose.Schema({
    name: String,
});

const Post = mongoose.model('Post', postSchema);
const Tag = mongoose.model('Tag', tagSchema);
```

### 1.4 Mối quan hệ n-n với bảng trung gian

-   Mối quan hệ n-n với bảng trung gian là mối quan hệ giữa hai bảng, trong đó mỗi bản ghi trong bảng này có thể liên kết với nhiều bản ghi trong bảng kia và ngược lại, nhưng có một bảng trung gian để lưu trữ mối quan hệ này.
-   Ví dụ: Một người dùng có thể tham gia nhiều nhóm và một nhóm có thể có nhiều người dùng.
-   Để thiết lập mối quan hệ n-n với bảng trung gian trong Mongoose, bạn có thể tạo một model mới để lưu trữ mối quan hệ này.

```javascript
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
    name: String,
    email: String,
});

const groupSchema = new mongoose.Schema({
    name: String,
    members: [
        {
            type: mongoose.Schema.Types.ObjectId,
            ref: 'User',
        },
    ],
});

const User = mongoose.model('User', userSchema);
const Group = mongoose.model('Group', groupSchema);
```

## 2. Truy vấn nâng cao

### 2.1. Lọc dữ liệu

-   Sử dụng `find()` để lọc dữ liệu theo điều kiện.

```javascript
const user = await User.find({ age: { $gt: 18 } });
```

### 2.2. Tìm kiếm dữ liệu

-   Sử dụng `find()` để tìm kiếm dữ liệu theo điều kiện.

```javascript
const user = await User.find({ name: { $regex: 'John', $options: 'i' } });
```

### 2.3. Sắp xếp dữ liệu

-   Sử dụng `sort()` để sắp xếp dữ liệu theo điều kiện.

```javascript
const users = await User.find().sort({ age: -1 });
```

### 2.4. Phân trang

-   Sử dụng `skip()` và `limit()` để phân trang dữ liệu.

```javascript
const page = 1;
const limit = 10;
const skip = (page - 1) * limit;
const users = await User.find().skip(skip).limit(limit);
```

## 3. Deploy ứng dụng lên Render
