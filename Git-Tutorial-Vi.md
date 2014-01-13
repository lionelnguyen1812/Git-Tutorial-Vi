[link_gitbare]: http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/vi/ch03.html

Hướng dẫn sử dụng Git cho dự án Agile
=====================================

#Chơi với Git đi

Nhiều nhóm phát triển phần mềm đã chuyển đổi từ những hệ thống quản lý mã nguồn 
tập trung như Subversion sang hệ thống phân tán giống Git.

Loạt bài viết này nhằm mục đích giới thiệu một cái nhìn về hệ thống Git, những 
mã lệnh của nó cùng với guides để sử dụng trong thực tế. Nhóm của bạn hoàn toàn
có thể giữ nguyên phong cách làm việc của mình trong khi vẫn có được những lợi 
ích từ sự nhẹ nhàng và nhiều tính năng mà Git mang tới.

#Hướng dẫn Git

##Git Cơ bản

Loạt bài đầu tiên - "Git cơ bản" cung cấp khái quát ngắn gọn về những mã lệnh
điều khiển quan trọng nhất của Git. Đầu tiên, section *Cài đặt một repo*
giải thích tất cả những công cụ cần thiết để bạn có thể bắt đầu một dự án quản
lý mã nguồn. Sau đó thì, section còn lại giới thiệu những lệnh điều khiển mà 
bạn sẽ thường xuyên sử dụng.

Đi theo tới phần cuối của chương này, bạn đã có thể tạo được một kho Git,
ghi một bản chụp nhanh của project của bạn cho mục đích an toàn, và xem lịch sử
sửa đổi của project của bạn.

###Khởi tạo một kho Git

Trong bản gốc của hướng dẫn này, từ "kho" trong tiếng Anh là "repository".
Tôi có thói quen gọi miệng là "bản chính" từ lúc còn chập chững học về Git. Có 
lẽ vì tôi thích tiền đề "mọi kho ở client đều là một kho của project". Bạn cho 
phép tôi gọi tắt repository là "kho" ở đây, bạn. Hi vọng bạn sẽ không khó chịu.

Dịch vụ lưu trữ kho Git lớn nhất hiện nay là **GitHub** cung cấp cho bạn một 
client Git với giao diện đồ họa rất đẹp và dễ dùng. Nhưng chỉ có trên Windows, 
dù thế tôi vẫn khuyến khích bạn tốt nhất sử dụng mã lệnh vì tính "mạnh" và 
"rõ ràng" của nó.

Về mặt cá nhân, tôi luôn có cảm giác bất khi nhấn nút **Sync** trên giao diện
điều khiển đồ họa của **GitHub**.

Để sử dụng được mã lệnh tốt, bạn nên trang bị cho mình một chút về các command
cơ bản như `dir`, `cd`, `cd ..`, `cd \`, `md`, ... (trên cmd của Windows) hay
`ls`, `mkdir`, `cd`, `rm`,... trên các hệ điều hành họ Unix/Linux.

####Lệnh `git init`

Lệnh `git init` sẽ tạo một kho Git mới trên thư mục hiện tại. Nó có thể dùng
để chuyển một project chưa được cung cấp sự quản lý phiên bản thành một bản
chính Git hoặc tạo ra một kho Git rỗng mới.

**Phần lớn các lệnh Git khác không cho phép chạy bên ngoài thư mục repo**
 (bản thân "repo" là một thư mục, nên tôi không viết là "thư mục chứa 
 repo"). Vì vậy gần như đây là lệnh Git đầu tiên bạn thực hiện trên một 
 project mới.

Chạy `git init` sẽ tạo ra một thư mục ẩn `.git` chứa các file metadata trong 
thư mục hiện hành. Ngoại trừ thư mục `.git`, những phần còn lại của
project sẽ không có gì thay đổi (không giống như SVN yêu cầu phải có một thư
mục metadata trong mỗi thư mục con).

**Sử dụng**

    git init

Chuyển thư mục hiện thành thành một kho Git. Hành động này tạo một thư 
mục ẩn `.git` vào thư mục hiện hành. Sau khi khởi tạo, kho ngay lập tức
sẵn sàng cho việc theo dõi các sửa đổi.

    git init <tên thư mục>

Tạo một thư mục với tên là <tên thư mục>, chuyển thư mục đó thành một bản 
chính Git, thư mục này sẽ chỉ chứa thư mục ẩn `.git`.

    git init --bare [<tên thư mục>]

khởi tạo một kho thuần. Tôi sẽ giải thích rõ hơn về kho thuần ngay sau đây.

**Thảo luận

Khi so sánh với SVN, lệnh `git init` quá sức đơn giản cho việc khởi tạo một 
repo mới. Git không hỏi gì thêm, không cần import file, không checkout đủ thứ.
Tất cả những gì cần làm là `cd` tới thư mục project và chạy `git init`. Sau đó
bạn đã có một kho Git với tất cả các chức năng mà hệ thống Git mang lại.

Dù sao, trong đa số project, `git init` chỉ cần chạy một lần để tạo repository 
trung tâm, những cộng tác viên khác không cần phải chạy `init` cho kho ở phía
máy tính của họ. Thay vì đấy, họ sẽ dùng `git clone` để tạo một bản sao về máy 
tính của mình.

**Repo thuần**

Gọi như vậy vì nó không chứa thư mục làm việc (tôi có tham khảo 
giải nghĩa này từ một bài dịch khác của tác giả Trần Ngọc Quân, các bạn có thể
xem bài viết gốc [ở đây][link_gitbare]). Nó chỉ chứa các tệp tin trong thư mục 
`.git`. Hay nó cách khác nó chứa lịch sử mã nguồn của một dự án, và không bao
giờ giữ các tập tin của bất kỳ phiên bản nào.

Kho thuần đóng vai trò hoạt động giống như máy chủ trung tâm trong SVN. Những 
sự biên soạn mã nguồn chỉ xảy ra trên những bản sao, vì thế thư mục chủ ở máy 
chủ trung tâm có thể hoạt động mà không cần thư mục làm việc. Điều này có nghĩa
là khi mô hình hóa luồng làm việc trên Git, ta có kho trung tâm sẽ là kho-thuần,
trong khi những kho địa phương trên máy của các cộng tác việc là 
kho-không-thuần.

![](git-tutorial-basics-init-barrepositories.png)

**Ví dụ**

Nếu giải nghĩa về kho thuần làm bạn rối trí. Hãy đừng lo. Việc khởi tạo kho 
thuần có thể được dịch vụ lưu trữ kho Git mà bạn dùng thực hiện tự động. Mà
dịch vụ web của GitHub là một ví dụ. Trong một trường hợp khác nào đó, quá 
trình tạo kho thuần vào máy chủ trung tâm trông sẽ giống như dưới đây

    ssh @
    cd path/above/repo
    git init --bare my-project.git

Câu lệnh đầu tiên sẽ SSH vào máy chủ sẽ chứa kho git trung tâm. Sau đó bạn `cd` 
thư mục chứa project. Và câu lệnh cuối cùng sử dùng cờ `--bare` để tạo một kho
thuần. Những cộng tác viên sau đó đã có thể dùng lệnh `git clone my-project.git`
để tạo một bản sao địa phương trên máy tính của họ.

####Lệnh `git clone`

Lệnh `git clone` giúp nhân bản một kho Git đã được init. Hành động này trông 
tương tự với `svn checkout`, nhưng tôi có thể giải thích rõ hơn ở đây, bạn hãy 
nghĩ về sự khác nhau giữa "nhân bản" với "yêu cầu cung cấp". Với Git, bản sao 
lấy về giống y hệt bản sao ở máy chủ trung tâm. Tất cả những gì có thể làm được
trên bản chính thì cũng có thể làm với bản sao. Bản sao cũng có mọi thứ của kho
chính, có lịch sử sửa đổi của riêng nó, bạn có thể quản lý mã nguồn với riêng 
nó, hoàn toàn biệt lập với kho chính.

Như một tiện ích, việc clone sẽ tự động tạo ra một thứ gọi là "nguồn gốc" (nguyên 
bản: origin), thứ này chỉ trở lại kho gốc. Sự tồn tại của "nguồn gốc" giúp Git 
dễ dàng tương tác với kho trung tâm và hoàn thiện sự "giống một cách hoàn hảo" 
của bản sao so với bản chính.

**Sử dụng**

    git clone <repo>

Nhân bản một kho Git tồn tại ở địa chỉ `<repo>` vào thư mục hiện hành. Kho gốc 
có thể tồn tại trên hệ thống địa phương hoặc trên máy chủ từ xa mà truy cập 
thông qua giao thức HTTP hoặc SSH.

    git clone <repo> <derectory>

Nhân bản kho Git <repo> tới thư mục <directory> ở máy địa phương.

**Thảo luận**

Nếu một project đã được cài đặt vào máy chủ trung tâm, lệnh `git clone` là cách 
thông dụng nhất để tạo bản sao. Giống như `git init`, nhân bản thường chỉ cần 
làm một lần vào lúc cộng tác viên yêu cầu cần có bản sao, sau đó mọi hành động 
quản lý phiên bản và cộng tác sẽ được quản lý trên kho địa phương của họ.

**Cộng tác trực tiếp Từ-Kho-Đến-Kho**













































