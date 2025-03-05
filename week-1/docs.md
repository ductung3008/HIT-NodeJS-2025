# Buổi 1: Tổng quan về Node.js & Ôn tập JavaScript

## 1. Tổng quan về [Node.js](https://nodejs.org/en/)

### 1.1. Giới thiệu về Node.js

-   Node.js là gì?

    -   Node.js là môi trường chạy JavaScript phía server, được xây dựng dựa trên [V8 Engine](https://v8.dev/) của Google Chrome.
    -   Node.js cho phép chạy JavaScript ngoài môi trường trình duyệt.
    -   Node.js được sử dụng để xây dựng các ứng dụng web, server, tools, ...

-   Tại sao chọn Node.js?

    -   JavaScript là ngôn ngữ phổ biến nhất thế giới.
    -   Cộng đồng lớn mạnh, nhiều thư viện hỗ trợ.
    -   Cơ chế Non-blocking I/O giúp xử lý nhiều request cùng lúc.

-   Ứng dụng của Node.js

    -   Xây dựng backend API (RESTful API, GraphQL API, ...)
    -   Xây dựng ứng dụng real-time (Chat, WebSocket, ...)

### 1.2. Cài đặt Node.js

-   Truy cập trang chủ [Node.js](https://nodejs.org/en/), tải bản mới nhất để cài đặt.
-   Kiểm tra Node.js và npm đã cài đặt thành công chưa:

    ```bash
    node -v
    npm -v
    ```

## 2. Ôn tập JavaScript (ES6+)

### 2.1. Destrucuring & Spread Operator

-   [Desctrucuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

    ```javascript
    const person = {
        name: 'Nguyen Van A',
        age: 18,
        address: {
            city: 'Ha Noi',
            country: 'Viet Nam',
        },
    };

    const {
        name,
        age,
        address: { city, country },
    } = person;
    console.log(name, age, city, country);
    ```

-   [Spread Operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

    ```javascript
    const arr1 = [1, 2, 3];
    const arr2 = [4, 5, 6];
    const mergedArr = [...arr1, ...arr2];
    console.log(mergedArr);
    ```

### 2.2. [Array Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

-   `push()`, `pop()`, `shift()`, `unshift()`: Thêm/xóa phần tử ở đầu/cuối mảng.

    ```javascript
    const arr = [1, 2, 3];
    arr.push(4); // [1, 2, 3, 4]
    arr.pop(); // [1, 2, 3]
    arr.shift(); // [2, 3]
    arr.unshift(0); // [0, 2, 3]
    ```

-   `forEach()`, `map()`, `filter()`: Duyệt mảng.

    ```javascript
    const arr = [1, 2, 3];
    arr.forEach((item) => console.log(item));
    const newArr = arr.map((item) => item * 2);
    const filteredArr = arr.filter((item) => item > 1);
    ```

-   `reduce()`: Tính toán giá trị từ mảng.

    ```javascript
    const arr = [1, 2, 3];
    const sum = arr.reduce((acc, item) => acc + item, 0);
    ```

-   `find()`, `findIndex()`: Tìm phần tử đầu tiên/cuối cùng thỏa mãn điều kiện.

    ```javascript
    const arr = [1, 2, 3];
    const foundItem = arr.find((item) => item > 1);
    const foundIndex = arr.findIndex((item) => item > 1);
    ```

-   `includes()`, `every()`, `some()`: Kiểm tra mảng.

    ```javascript
    const arr = [1, 2, 3];
    const isIncluded = arr.includes(2);
    const isEvery = arr.every((item) => item > 1);
    const isSome = arr.some((item) => item > 1);
    ```

### 2.3. [String Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

-   `split()`, `join()`: Tách/Nối chuỗi.

    ```javascript
    const str = 'Hello, World';
    const arr = str.split(', '); // ['Hello', 'World']
    const newStr = arr.join(' - '); // 'Hello - World'
    ```

-   `includes()`, `startsWith()`, `endsWith()`: Kiểm tra chuỗi.

    ```javascript
    const str = 'Hello, World';
    const isIncluded = str.includes('Hello');
    const isStartsWith = str.startsWith('Hello');
    const isEndsWith = str.endsWith('World');
    ```

-   `toUpperCase()`, `toLowerCase()`, `trim()`: Định dạng chuỗi.

    ```javascript
    const str = ' Hello, World ';
    const upperStr = str.toUpperCase();
    const lowerStr = str.toLowerCase();
    const trimmedStr = str.trim();
    ```

### 2.4. [Object Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

-   `Object.keys()`, `Object.values()`, `Object.entries()`: Lấy thông tin từ Object.

    ```javascript
    const person = {
        name: 'Nguyen Van A',
        age: 18,
    };

    const keys = Object.keys(person);
    const values = Object.values(person);
    const entries = Object.entries(person);
    ```

-   `Object.assign()`: Gộp Object.

    ```javascript
    const person = {
        name: 'Nguyen Van A',
        age: 18,
    };

    const address = {
        city: 'Ha Noi',
        country: 'Viet Nam',
    };

    const personWithAddress = Object.assign({}, person, address);
    ```
