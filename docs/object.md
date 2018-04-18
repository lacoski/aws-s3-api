# Làm việc với s3 object

S3 object là cặp giá trị "key:value". Có thể lưu object trong 1 hoặc nhiều object

# Khái niệm:
- Key: tên gán cho object
- Version ID: bên trong bucket, key và version ID độc nhất trên toàn bucket.
- Value: Nội dung object, có thể là bất kỳ chuỗi byte nào. Giá trị từ 0 => 5TB.
- Metadata: Tập các cặp "key:value" lưu thông tin về object, chứa các thông tin liên quan đến object. Có thể gắn metadata custom (user định nghĩa), sử dụng nó để quản lý các objects.
- Subresources: S3 sử dụng kỹ thuật subresource để lưu obj nhất định với thông tin được mở rộng


# Object Key and Metadata
- Mỗi object có data, key, Metadata
- object key (key name) đọc nhất trên toàn bucket. Object metadata là tập các cặp "key:value".
- Chỉ có thể gán metadata trươc khi upload. Sau khi upload object, không thể gắn thêm metadata.

## Object Keys
- Khi tạo object, có thể chỉ định keyname, có định danh động nhất trên bucket.

## Quy tắc đặt trên object keys
- Có thê rsuwr dụng bất kỳ ký tự thuộc UTF-8 đối với object key name
- Quy tắc đặt trên tốt nhất là tương thích theo app. Mỗi app có thể đọc ký tự khác biệt.

## Safe Characters
- Các ký tự nên sử dụng:
 - Alphanumeric characters [0-9a-zA-Z]
 - Special characters `!, -, _, ., *, ', (, and )`

VD:
```
4my-organization

my.great_photos-2014/jan/myvacation.jpg

videos/2014/birthday/video1.wmv
```

Kiên trúc S3 theo quy tắc:
- Tạo bucket, lưu bucket stores objects.
- Không có phân cấp, cấu trúc subfolder. Tuy nhiên, ta có thể giả sự phân cấp = các tiền tố `.`, `/`, `,` để tạo ra sự phân cấp.

VD:
```
Development/Projects1.xls
```

## Các ký tự yêu cầu xử lý đặc biêt:
> Liên quan đế xử lý code và phân giải URL
pic 1

## Các ký tự cần tránh
pic 2
---

# Object Metadata
Có 2 loại metadata:
- system metadata
- user-defined metadata.

## System-Defined Metadata
- Mỗi object lưu trong object, S3 đều set 1 tập các system metadata. S3 xử lý các metadata này khi cần thiết.

VD: S3 Duy trì thời gian tạo, size metadata sử dụng các giá trị này để quản trị object.

Có 2 loại metadata trong system metadata:
- Metadata như thời gian tạo, system sẽ kiểm soát, chỉ có S3 mới có khả năng sử đổi giá trị
- System metadata, như storage class config, các server side encrypd, ..

## User-Defined Metadata
- khi upload object, user có thể gán metadata cho object. Cung cấp các thông tin tùy chọn như các cập "name-value" khi PUST, POST request.

# Object Versioning
- Sử dụng version để giữ các phiên bản object trong bucket.

VD: có thể lưu trữ 2 phiên bản khác nhau trong cùng 1 object.
- Version 1: images.jpg
- Version 2: images.jpg
Nguồn tham khảo thêm

https://docs.aws.amazon.com/AmazonS3/latest/dev/ObjectVersioning.html




# Nguồn
https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingMetadata.html
