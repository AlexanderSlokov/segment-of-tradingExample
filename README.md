# segment-of-tradingExample
Repo sub-directory for segment module of tradingExample repo

Để sử dụng Git Submodules để quản lý truy cập riêng biệt cho thư mục `segment` mà không cho phép người khác truy cập vào thư mục `models` trong dự án của bạn, bạn có thể tách `segment` ra thành một submodule riêng. Dưới đây là các bước cần thực hiện:

### Bước 1: Tạo một kho lưu trữ mới cho submodule
Vâng, bạn hoàn toàn có thể tạo một kho lưu trữ (repo) mới rỗng trên GitHub, GitLab hoặc Bitbucket để làm kho cho submodule. Sau khi tạo kho rỗng, bạn chỉ cần push nội dung của thư mục `segment` vào kho này. Đây là các bước cơ bản để làm điều đó:

1. Truy cập vào một trong các nền tảng (GitHub, GitLab, hoặc Bitbucket) và tạo một kho lưu trữ mới.
2. Khởi tạo kho lưu trữ trên máy tính của bạn (nếu bạn đã có thư mục `segment` với các tệp tin cần thiết, bạn có thể bỏ qua bước khởi tạo và chỉ cần cài đặt kho lưu trữ từ xa).
3. Đặt kho lưu trữ vừa tạo làm kho lưu trữ từ xa (remote) cho thư mục `segment`:
   ```bash
   cd segment
   git init
   git remote add origin <URL-to-your-new-repository>
   ```
4. Thêm tất cả các tệp tin trong thư mục `segment` vào kho lưu trữ:
   ```bash
   git add .
   git commit -m "Initial commit"
   ```
5. Push nội dung lên kho lưu trữ từ xa:
   ```bash
   git push -u origin master
   ```

Bằng cách này, bạn đã sẵn sàng để sử dụng thư mục `segment` như một submodule trong dự án chính của mình.

### Bước 2: Loại bỏ thư mục `segment` khỏi kho lưu trữ chính
Trước khi bạn thêm `segment` như một submodule, bạn cần loại bỏ nó khỏi kho lưu trữ chính để tránh xung đột. Đây là cách bạn thực hiện:

1. Di chuyển vào thư mục chính của dự án của bạn.
2. Xóa thư mục `segment` khỏi kho lưu trữ nhưng giữ lại trên máy tính của bạn:
   ```bash
   git rm -r --cached segment
   git commit -m "Remove segment directory"
   ```

### Bước 3: Thêm thư mục `segment` như một submodule
Sau khi thư mục `segment` đã được loại bỏ khỏi kho lưu trữ chính, bạn có thể thêm nó trở lại như một submodule bằng cách sử dụng địa chỉ kho lưu trữ mới của nó:

1. Thêm submodule:
   ```bash
   git submodule add <URL-of-segment-repository> segment
   ```
   Thay thế `<URL-of-segment-repository>` với đường dẫn thực tế đến kho lưu trữ mới của thư mục `segment`.

2. Khởi tạo submodule và cập nhật:
   ```bash
   git submodule init
   git submodule update
   ```

### Bước 4: Quản lý quyền truy cập
- **Quản lý quyền truy cập của kho lưu trữ `segment`**: Bạn có thể quản lý quyền truy cập trên GitHub, GitLab, hoặc Bitbucket bằng cách chỉ định những người dùng hoặc nhóm có quyền đẩy (push) hoặc kéo (pull) từ kho lưu trữ này.
- **Giữ an toàn cho thư mục `models`**: Đảm bảo rằng chỉ những người dùng có quyền truy cập cần thiết mới có thể xem hoặc sửa đổi nội dung trong thư mục `models`.

### Bước 5: Làm việc với Submodule
Khi bạn làm việc với submodules, các thay đổi trong thư mục `segment` sẽ cần được đẩy (push) lên kho lưu trữ riêng của nó, và bạn cũng cần cập nhật thường xuyên submodule trong kho lưu trữ chính để đảm bảo rằng bạn đang làm việc với phiên bản mới nhất.

Bằng cách này, bạn có thể quản lý quyền truy cập một cách hiệu quả, đồng thời giữ cho thư mục `segment` dễ dàng truy cập cho những người cần nó mà không ảnh hưởng đến các phần khác của dự án.
