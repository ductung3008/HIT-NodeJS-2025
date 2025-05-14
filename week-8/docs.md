# Buổi 8: Upload file bằng Multer trong Express.js

## 1. Giới thiệu Multer

### 1.1 Multer là gì?

-   Multer là một middleware cho Express.js, giúp xử lý `multipart/form-data`, định dạng dữ liệu thường được sử dụng để upload file.
-   Multer cho phép bạn dễ dàng nhận và xử lý file upload từ client, lưu trữ chúng vào hệ thống tệp hoặc cơ sở dữ liệu.
-   Multer hỗ trợ nhiều tùy chọn cấu hình, cho phép bạn kiểm soát cách thức lưu trữ và xử lý file upload.

### 1.2 Khi nào nên sử dụng Multer?

-   Khi bạn cần upload file từ client đến server trong ứng dụng web.
-   Khi bạn muốn xử lý file upload một cách dễ dàng và hiệu quả trong ứng dụng Express.js.
-   Khi bạn cần kiểm soát các thuộc tính của file upload như kích thước, loại file, tên file, v.v.

## 2. Cài đặt Multer

```
npm install multer
```

## 3. Cấu hình Multer

## 3.1. Tạo middleware Multer

```javascript
const path = require('path');
const multer = require('multer');
const httpStatus = require('http-status-codes');

const ApiError = require('../utils/ApiError');

const limitSize = 5 * 1024 * 1024; // Giới hạn kích thước file upload (5MB)

const storage = multer.diskStorage({
    destination: function (req, file, cb) {
        cb(null, 'uploads'); // Thư mục lưu trữ file upload
    },
    filename: function (req, file, cb) {
        const ext = file.originalname.split('.').pop(); // Lấy phần mở rộng của file
        cb(null, file.fieldname + '-' + Date.now() + '.' + ext); // Tạo tên file duy nhất
    },
});

const fileFilter = (req, file, cb) => {
    const allowedTypes = ['image/jpeg', 'image/png', 'image/gif']; // Các loại file được phép upload
    if (!allowedTypes.includes(file.mimetype)) {
        return cb(
            new ApiError(
                httpStatus.BAD_REQUEST,
                'Chỉ cho phép upload file hình ảnh'
            ),
            false
        );
    }
    cb(null, true);
};

const upload = multer({
    storage, // Cấu hình lưu trữ file
    fileFilter, // Kiểm tra loại file
    limits: {
        fileSize: limitSize, // Giới hạn kích thước file
    },
});

module.exports = upload;
```

## 3.2. Sử dụng middleware Multer trong route

```javascript
app.post('/upload', upload.single('file'), (req, res) => {
    if (!req.file) {
        return res.status(httpStatus.BAD_REQUEST).json({
            statusCode: httpStatus.BAD_REQUEST,
            message: 'Không có file nào được upload',
        });
    }

    res.status(httpStatus.OK).json({
        statusCode: httpStatus.OK,
        message: 'Upload file thành công',
        data: {
            file: req.file,
        },
    });
});
```
