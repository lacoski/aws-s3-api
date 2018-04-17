# Overview amazon S3 and Guide
amazon s3 là giao diện web service đơn giản, cho phép lưu trữ data, lấy lại, truy cấp bất kỳ điểm nào.

Điểm mạnh Amazon s3
- xây dựng các tính năng đơn giản nhất, tiện ích nhất.

1 số điểm manhk chính của Amazon S3 service:
- Create Buckets: Tạo, đặt tên Bucket lưu trữ data. Bucket là thành phần cơ bản để lưu trữ dữ liệu tới Data storage
- Store data in Buckets: data được lưu trữ không giới hạn trong bucket, upload nhiều nhất có thể tới Amazon s3 bucket, mỗi object có giới hạn cao nhất là 5TB. Mỗi Object được lưu và lấy lại dựa trên định danh riêng biệt (developer gán key định danh)
- Download data: Tải data hoặc cho phép người khác tải.
- Quyền: Cho phép hoặc block user truy cập tới own Amazon s3 bucket. Cấp quyền upload, down tới 3 loại user, kỹ thuật chứng thực giúp data bảo đảm bởi các truy cập trái phép
- Giao diện chính: Xây dựng dựa trên Rest và SOAP, thiết kế làm việc với nhiều môi trường (internet,..)

Note:
- SOAP không khuyến cáo chạy trên HTTP, nhưng nó vấn có thể chạy trên HTTPS. Các tính năng mới s3 không được hỗ trợ trên SOAP. Khuyển cáo sử dụng REST API or AWS SDKs

# Buckets
- Khối các object được lưu tại amazon s3, tất cả object được chứa trong bucket.

VD: Nếu object đặt trên "photos/puppy.jpg" trong `johnsmith` => truy cập trên url http://johnsmith.s3.amazonaws.com/photos/puppy.jpg

Bucket phục vụ cho 1 số mục đích:
- Tổ chúc Amazon s3 namespace tại lvl cao nhất, xác thực acc chịu trách nhiện cho storage và data

Objects:
- object đối tượng căn bản lưu trữ data trên AmazonS3.
- object bao gồm object + metadata.
-- metadata là tập các cặp name-value mô tả object. Chúng bao gồm 1 số metadata default như lần sửa cuối, chuẩn http metadata (content-type), có thể custom metadata tại thời điểm lưu

- object có định danh riêng trong bucket = key(name) + ver ID.

# Key
- định danh riêng cho object trong bucket, tất cả object trong bucket có 1 key.
- định danh object dựa trên (bucket, key, verid). Tất cả object trong Amazon được lưu tại ví trị riêng biệt trong Amazon s3.
VD:
http://doc.s3.amazonaws.com/2006-03-01/AmazonS3.wsdl - "doc" is the name of the bucket and "2006-03-01/AmazonS3.wsdl" is the key.

Regions
- bỏ qua (tối ưu tại từng cụm amazon, ở đây dùng ceph thay thế)

Amazon S3 Data Consistency Model
- amazon s3 cung cấp tinh read-after-write khi PUTS 1 object mới tới s3 bucket
- s3 cung cấp sự nhất quan khi gi đè PUTs và delete.

```
A process writes a new object to Amazon S3 and immediately lists keys within its bucket. Until the change is fully propagated, the object might not appear in the list.

A process replaces an existing object and immediately attempts to read it. Until the change is fully propagated, Amazon S3 might return the prior data.

A process deletes an existing object and immediately attempts to read it. Until the deletion is fully propagated, Amazon S3 might return the deleted data.

A process deletes an existing object and immediately lists keys within its bucket. Until the deletion is fully propagated, Amazon S3 might list the deleted object.
```

# Operations
Hoạt động thường gặp
- Create a Bucket – Create and name your own bucket in which to store your objects.
- Write an Object – Store data by creating or overwriting an object. When you write an object, you specify a unique key in the namespace of your bucket. This is also a good time to specify any access control you want on the object.
- Read an Object – Read data back. You can download the data via HTTP or BitTorrent.
- Deleting an Object – Delete some of your data.
- Listing Keys – List the keys contained in one of your buckets. You can filter the key list based on a prefix.
- Details on this and all other functionality are described in detail later in this guide
