# Bài 1: Phân tích HTTP Request và Response

## 1. Thành phần của HTTP Request

### Method
- `POST`
- Dùng để tạo mới tài nguyên trên server.

### URL
- `/api/sanpham`
- Endpoint nhận yêu cầu tạo sản phẩm.

### Headers

| Header | Ý nghĩa |
|----------|----------|
| Host: example.com | Tên miền của server |
| Content-Type: application/json | Dữ liệu gửi lên ở định dạng JSON |
| Authorization: Bearer abc123 | Token xác thực người dùng |
| Content-Length: 48 | Kích thước body (48 bytes) |

### Body

```json
{
  "ten": "Laptop",
  "gia": 15000000,
  "tonkho": 10
}
```

Chứa dữ liệu sản phẩm cần tạo.

---

## 2. Thành phần của HTTP Response

### Status Line

```http
HTTP/1.1 201 Created
```

- `201 Created` thuộc nhóm **2xx (Success)**.
- Ý nghĩa: Server đã tạo thành công tài nguyên mới.

### Headers

| Header | Ý nghĩa |
|----------|----------|
| Date | Thời gian phản hồi |
| Content-Type: application/json | Dữ liệu trả về là JSON |
| Location: /api/sanpham/101 | URL của tài nguyên vừa được tạo |

### Body

```json
{
  "id": 101,
  "ten": "Laptop",
  "gia": 15000000,
  "tonkho": 10
}
```

Thông tin sản phẩm sau khi được tạo.

---

## 3. GET `/api/sanpham/999` nhưng sản phẩm không tồn tại

Mã trạng thái:

```http
404 Not Found
```

Ý nghĩa:
- Server nhận request thành công.
- Không tìm thấy tài nguyên có ID = 999.

---

## 4. Lỗi xử lý không xác định trên Server

Mã trạng thái thường dùng:

```http
500 Internal Server Error
```

Ý nghĩa:
- Server gặp lỗi trong quá trình xử lý request.
- Client gửi request hợp lệ nhưng server không xử lý được.
