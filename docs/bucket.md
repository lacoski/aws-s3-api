# Làm việc với bucket

Theo thuật ngữ chung, bucket và object là các tài nguyên, trong đó, bucket chứa các object.

S3 cung cấp api cho phép quản trị.

VD:
- Tạo bucket
- Upload object sử dụng Amazon S3 API.
- S3 bucket

Tên các s3 bucket độc nhất, bất kể thuộc AWS Region tạo bucket. Vì vậy cần xác định thười gian tạo bucket. (Xem thêm gui các đặt tên bucket)

# Hạn chế
- Quyền sử hữu bucket không thể chuyển, nếu bucket trống có thể xóa => tên sẽ sẵn sàng để tạo lại mới

Không có giới hạn object có thể lưu trong bucket, có thể lưu object trong 1 bucket hoặc nhiều bucket.

Rules for Bucket Naming
- Tên bucket cần độc nhất trên toàn bộ bucket có sẵn.

Tên bucket tuân theo:
- ít nhất 3 ký tự, tối đa 63 ký tự
- Tên bucket có thể có 1 hoặc nhiều label. Các label phân chia = dấu '.'
 VD: "abc.xyz"
- Tên bucket không được đặt dạng IP: x.x.x.x

VD:
```
.myawsbucket	       Bucket name cannot start with a period (.).
myawsbucket.	       Bucket name cannot end with a period (.).
my..examplebucket	   There can be only one period between labels.
```


Các hoạt động trên bucket: (docs boto)
- Creating a Bucket
- Accessing a Bucket
- Bucket Configuration Options
- Bucket Restrictions and Limitations
- Examples of Creating a Bucket
- Deleting or Emptying a Bucket
