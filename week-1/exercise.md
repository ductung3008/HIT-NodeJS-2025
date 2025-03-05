## Bài 1:

```javascript
let products = [
    {
        id: 1,
        name: 'Sony Xperia XZ',
        price: 100,
        brand: 'Sony',
    },
    {
        id: 2,
        name: 'Samsung Galaxy S7',
        price: 200,
        brand: 'Samsung',
    },
    {
        id: 3,
        name: 'Iphone 6',
        price: 300,
        brand: 'Apple',
    },
    {
        id: 4,
        name: 'Iphone 7',
        price: 400,
        brand: 'Apple',
    },
];
```

1. Tạo sản phẩm mới rồi thêm vào mảng `products` với thông tin như sau:
    - id: 5
    - name: 'Xiaomi Redmi Note 4'
    - price: 150
    - brand: 'Xiaomi'
2. Xóa sản phẩm có tên `Samsung Galaxy S7`
3. Tìm kiếm sản phẩm có id = 4 và in ra thông tin
4. Sắp xếp các sản phẩm theo giá từ cao xuống thấp và in
5. Tính tổng giá trị của các sản phẩm và in ra

## Bài 2:

```javascript
const users = [
    {
        id: 1,
        name: 'Nguyen Van A',
        age: 20,
        address: 'Ha Noi',
    },
    {
        id: 2,
        name: 'Tran Thi B',
        age: 25,
        address: 'Ho Chi Minh',
    },
    {
        id: 3,
        name: 'Le Thi C',
        age: 30,
        address: 'Da Nang',
    },
    {
        id: 4,
        name: 'Pham Van D',
        age: 35,
        address: 'Hai Phong',
    },
    {
        id: 5,
        name: 'Hoang Van E',
        age: 40,
        address: 'Ho Chi Minh',
    },
    {
        id: 6,
        name: 'Tran Thi F',
        age: 45,
        address: 'Nha Trang',
    },
];
```

1. Lọc ra những người có tuổi lớn hơn hoặc bằng 30
2. Tìm người đầu tiên sống tại `Ho Chi Minh`
3. Kiểm tra xem có ai trên 50 tuổi không
4. Lấy danh sách tên của mọi người và in ra

## Bài 3:

1. Tạo mảng `numbers` gồm 10 số nguyên dương ngẫu nhiên (từ 1 đến 100)
2. Lọc ra các số chia hết cho 3
3. Tìm số lớn nhất và nhỏ nhất
4. Tính tổng các số trong mảng

## Bài 4:

```javascript
const customers = [
    {
        id: 1,
        name: 'Nguyen Van A',
        age: 20,
        address: 'Ha Noi',
        orders: [
            {
                id: 1,
                name: 'Iphone 6',
                price: 300,
                quantity: 2,
            },
            {
                id: 2,
                name: 'Iphone 7',
                price: 400,
                quantity: 1,
            },
        ],
    },
    {
        id: 2,
        name: 'Tran Thi B',
        age: 25,
        address: 'Ho Chi Minh',
        orders: [
            {
                id: 3,
                name: 'Samsung Galaxy S7',
                price: 200,
                quantity: 1,
            },
        ],
    },
    {
        id: 3,
        name: 'Le Thi C',
        age: 30,
        address: 'Da Nang',
        orders: [
            {
                id: 4,
                name: 'Sony Xperia XZ',
                price: 100,
                quantity: 3,
            },
        ],
    },
    {
        id: 4,
        name: 'Pham Van D',
        age: 35,
        address: 'Hai Phong',
        orders: [
            {
                id: 5,
                name: 'Xiaomi Redmi Note 4',
                price: 150,
                quantity: 2,
            },
        ],
    },
    {
        id: 5,
        name: 'Hoang Van E',
        age: 40,
        address: 'Ho Chi Minh',
        orders: [
            {
                id: 6,
                name: 'Iphone 6',
                price: 300,
                quantity: 1,
            },
            {
                id: 7,
                name: 'Iphone 7',
                price: 400,
                quantity: 1,
            },
        ],
    },
    {
        id: 6,
        name: 'Tran Thi F',
        age: 45,
        address: 'Nha Trang',
        orders: [
            {
                id: 8,
                name: 'Samsung Galaxy S7',
                price: 200,
                quantity: 1,
            },
            {
                id: 9,
                name: 'Sony Xperia XZ',
                price: 100,
                quantity: 2,
            },
        ],
    },
];
```

1. Tạo một danh sách mới với tổng số tiền mỗi khách hàng đã chi tiêu.
2. Lọc ra những khách hàng có tổng chi tiêu lớn hơn 300
3. Tìm những khách hàng có tổng chi tiêu nhỏ nhất
4. Kiểm tra xem có khách hàng nào chưa mua sản phẩm nào không
