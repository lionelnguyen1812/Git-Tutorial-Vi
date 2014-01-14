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

#####Sử dụng

    git init

Chuyển thư mục hiện thành thành một kho Git. Hành động này tạo một thư 
mục ẩn `.git` vào thư mục hiện hành. Sau khi khởi tạo, kho ngay lập tức
sẵn sàng cho việc theo dõi các sửa đổi.

    git init <tên thư mục>

Tạo một thư mục với tên là <tên thư mục>, chuyển thư mục đó thành một bản 
chính Git, thư mục này sẽ chỉ chứa thư mục ẩn `.git`.

    git init --bare [<tên thư mục>]

khởi tạo một kho thuần. Tôi sẽ giải thích rõ hơn về kho thuần ngay sau đây.

#####Thảo luận

Khi so sánh với SVN, lệnh `git init` quá sức đơn giản cho việc khởi tạo một 
repo mới. Git không hỏi gì thêm, không cần import file, không checkout đủ thứ.
Tất cả những gì cần làm là `cd` tới thư mục project và chạy `git init`. Sau đó
bạn đã có một kho Git với tất cả các chức năng mà hệ thống Git mang lại.

Dù sao, trong đa số project, `git init` chỉ cần chạy một lần để tạo repository 
trung tâm, những cộng tác viên khác không cần phải chạy `init` cho kho ở phía
máy tính của họ. Thay vì đấy, họ sẽ dùng `git clone` để tạo một bản sao về máy 
tính của mình.

#####Repo thuần

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

![](/images/git-tutorial-basics-init-barrepositories.png)

#####Ví dụ

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

#####Sử dụng

    git clone <repo>

Nhân bản một kho Git tồn tại ở địa chỉ `<repo>` vào thư mục hiện hành. Kho gốc 
có thể tồn tại trên hệ thống địa phương hoặc trên máy chủ từ xa mà truy cập 
thông qua giao thức HTTP hoặc SSH.

    git clone <repo> <derectory>

Nhân bản kho Git <repo> tới thư mục <directory> ở máy địa phương.

#####Thảo luận

Nếu một project đã được cài đặt vào máy chủ trung tâm, lệnh `git clone` là cách 
thông dụng nhất để tạo bản sao. Giống như `git init`, nhân bản thường chỉ cần 
làm một lần vào lúc cộng tác viên yêu cầu cần có bản sao, sau đó mọi hành động 
quản lý phiên bản và cộng tác sẽ được quản lý trên kho địa phương của họ.

#####Cộng tác trực tiếp Từ-Kho-Đến-Kho

Một điểm rất quan trọng cần phải hiểu rõ đó là ý tưởng về "bản sao" của Git rất
khác so với bản sao được checkout về từ kho SVN. Không giống SVN, Git không có
sự khác biệt nào giữa bản sao hiện hành (là bản sao ở phía các cộng tác viên) và
bản chính ở kho trung tâm - như tôi đã nhấn mạnh ở phần trước, tất cả những gì 
thực hiện được với kho trung tâm thì cũng làm được trên bản sao.

Sự khác biệt này khiến cho làm việc cộng tác với Git về cơ bản khác hoàn toàn 
khi so với SVN. Trong khi SVN phụ thuộc vào mối liên hệ giữa bản sao và kho 
trung tâm, sự cộng tác ở Git dựa trên sự ảnh hưởng của từng kho (hay là từng 
bản sao (hay cũng có thể gọi là bản chính?)) với nhau. Thay vì kiểm tra bản sao
hiện hành vào kho chính SVN, ở Git bạn `push` hoặc `pull` những `commit` từ một 
kho này tới một kho khác.

![](/images/git-tutorial-basics-init-barrepositories.png)

Dĩ nhiên, không có điều gì cản trở bạn chỉ định rõ một kho Git duy nhất để đồng
bộ. Ví dụ như, bằng việc đơn giản là thiết kế một kho Git nào đó như là kho 
"trung tâm", sẽ cho phép nhóm của bạn triển khai mô hình "Luồng làm việc với 
kho trung tâm" - có điều là, điểm này, dùng Git, và hoàn toàn bằng các quy ước 
chứ không phải là "bắt buộc phải làm thế" giống như khi sử dụng VCS.

#####Ví dụ

Ví dụ dưới đây cho các bạ thấy làm thế nào để lấy về một bản sao của kho trung 
tâm trên một máy chủ mà cho phép truy cập bằng địa chỉ `example.com` chứng thực
thông qua giao thức SSH với username `john`.

    git clone ssh://john@example.com/path/to/my-project.git
    cd my-project
    # Bắt đầu làm việc với project của bạn, trên-máy-của-bạn.

Câu lệnh đầu tiên sẽ cài đặt một kho Git mới vào folder mới có cùng tên với file 
`.git` (ở đây sẽ là `my-project`) trên thư mục hiện hành của bạn. Câu lệnh thứ 
hai cd vào project và bạn có thể ngay lập tức bắt đầu chỉnh sửa các tài liệu, 
ghi lại một trạng thái, hay giao dịch với một kho khác. Cũng cần nói thêm là 
file `.git` được bỏ qua ở các kho nhân bản. Việc này phản ánh tính chất 
không-thuần của bản sao địa phương.

####Lệnh `git config`

Lệnh `git config` cho phép bạn cấu hình trình bộ cài đặt Git của bạn (hoặc một 
kho Git cá nhân của bạn). Lệnh này có thể xác định tất cả mọi thứ từ thông tin 
người sử dụng đến hành vi của kho lưu trữ. Một vài cài đặt thông dụng được liệt
kê dưới đây.

#####Sử dụng

    git config user.name <name>

Định rõ tên tác giả sẽ được dùng để kê khai vào lịch sử ghi trạng thái của kho 
hiện hành. Có thể bạn sẽ muốn dùng cờ `--global` để triển khai cài đặt này cho 
mọi ghi chép ở những kho khác (việc này chỉ giới hạn cho user mà bạn đang dùng
để đăng nhập hệ điều hành). Sau đây là cách làm:

    git config --global user.name <name>

Định tên tác giả để kê khai vào lịch sử những commit được thực hiện bởi user 
hiện tại.

    git config --global user.email <email>

Định rõ email tác giả với mục đích tương tự như với user.name.

    git config --global alias.<alias-name> <git-command>

Định nghĩa một shortcut cho một câu lệnh git.

    git config --system core.editor <editor>

Chỉ rõ text-editor mà trong một vài trường hợp, một số lệnh git sẽ sử dụng.
Cài đặt này có hiệu lực trên toàn hệ thống. Tham số `<editor>` cần phải chính
là lệnh mà có thể chạy editor từ chính terminal hay cmd (như là `notepad`,
'vi`, 'vim`, 'gedit',...).

    git config --global --edit

Dùng text-editor mở file config mà chứa những cài đặt toàn cục, để cài đặt thủ 
công.

#####Thảo luận

Mọi lựa chọn cài đặt của Git đều được chứa trong những file text thuần, do đó 
bản chất của `git config` chỉ là cung cấp cho bạn giao diện trực quan hơn để
sửa những khóa trong những file text đó. Thông thường bạn chỉ cần thực hiện 
cài đặt Git vào lần đầu tiên bạn làm việc với Git trên một máy tính mới, và 
trong đa số, bạn thường sẽ muốn dùng tới cờ `--global`.

Git chứa những cài đặt của nó trong 3 file riêng biệt nhau, cho phép bạn tách 
những cài đặt của cấp *kho*, *users*, và *toàn bộ hệ thống*.

* `<repo>/.git/config` (file config không có phần mở rộng) - Nằm trong thư mục
`.git` của mỗi kho. Chứa những cài đặt dành riêng cho kho đó.

* `~/.gitconfig` - Nằm trên thư mục riêng của mỗi user. Chứa những cài đặt toàn
cục mà được đặt với cờ `--global`.

* `$(prefix)/etc/gitconfig` - Chứa những cài đặt trên toàn hệ thống. Mọi chỉnh 
sửa trên file này chỉ có thể được thực hiện với quyền root ( tương đương với
Administrator trên Windows).

Khi những tùy chọn trong những file trên xung đột với nhau, tùy chọn nằm trên 
file "gần" với kho hơn sẽ được ưu tiên sử dụng. Nếu bạn mở bất kỳ một file 
config nào, bạn đều sẽ thấy những thứ tương tự như sau:

    [user] 
    name = John Smith
    email = john@example.com
    [alias]
    st = status
    co = checkout
    br = branch
    up = rebase
    ci = commit
    [core]
    editor = vim

Bạn có thể sửa trực tiếp những giá trị trong đó, hiệu lực của việc này tương 
đương với sử dụng lệnh `git config`.

#####Ví dụ

Điều đầu tiên bạn nên muốn làm sau khi cài đặt Git là chỉ định *username* và 
*email* của bạn, cùng với đó là một vài cài đặt mặc định. Một số cài đặt mà 
thông thường sẽ được thực hiện trông giống như dưới đây:

    #Tell Git who you are
    git config --global user.name "John Smith"
    git config --global user.email "john@example.com"

    #Select your favorite text-editor
    git config --global core.editor vim

    #Add some SVN-like aliases
    git config --global alias.st status
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.up rebase
    git config --global alias.ci commit

Những lệnh trên sẽ "làm gì đó" trên file `~/.gitconfig` đã được giới thiệu ở 
phần trước.

####Lệnh `git add`

Lệnh `git add` sẽ thêm một thay đổi trên kho hiện hành vào vùng theo dõi. Nó 
thông báo cho Git rằng bạn muốn bổ sung một cập nhật cho file được chỉ định 
trong lần commit tiếp theo. Dù sao, `git add` không thực sự ảnh hưởng tới kho 
theo bất kỳ nghĩa nào - những thay đổi chỉ thực sự được ghi lại khi mà bạn chạy
`git commit`.

Trong sự liên kết giữa những lệnh trên, bạn cũng sẽ cần dùng tới `git status` 
thường xuyên để xem trạng thái hiện tại của kho hiện hành cùng với khu vực đang
được theo dõi.

#####Sử dụng

    git add <file>

Đánh dấu theo dõi mọi thay đổi của <file> kể từ lần commit tiếp theo.

    git add <directory>

Đánh dấu theo dõi mọi thay đổi trong thư mục <directory> kể từ lần commit tiếp 
theo.

    git add -p

Bắt đầu một đoạn "đối thoại" mà trong quá trình đó bạn sẽ chọn ra những vị trí 
thay đổi của file để "add". Với mỗi thay đổi, Git sẽ cung cấp cho bạn một cơ số
lựa chọn, trả lời `y` để lưu khu vực thay đổi vào diện được theo dõi, `n` để bỏ
qua, `s` để chia khu vực thay đổi thành những phần nhỏ hơn, `e` để chỉnh sửa 
thủ công khu vực thay đổi, `a` để hủy thao tác và `q` để thoát.

#####Thảo luận

Lệnh `git add` và `git commit` tạo nên cơ sở cho luồng làm việc trên Git. Chúng
là hai lệnh và bất cứ người dùng Git nào cũng cần phải nắm vững, bất kể mô hình
cộng tác của team bạn ra sao. Chúng là những phương tiện để ghi lại các phiên 
bản của một project vào lịch sử của kho. 

Phát triển một dự án luôn xoay quanh các mô hình chỉnh sửa, giai đoạn và commit
cơ bản. Trước tiên, bạn chỉnh sửa các tệp tin trong thư mục hiện hành. Khi bạn
đã sẵn sàng để lưu một bản sao của trạng thái hiện tại của dự án, bạn đưa thay 
đổi đó lên mức độ "đã chấp nhận" bằng lệnh `git add`. Sau khi bạn đã cảm thấy 
OK với trạng thái hiện giờ của phiên bản, bạn cam kết nó vào lịch sử dự án với 
lệnh `git commit`. 

![](/images/git-tutorial-basics-add-addsnapshot.png)

Lệnh `git add` không tương đồng với `svn add` (cái mà ngay lập tức thêm tập tin
vào kho). Thay vào đó, `git add` làm việc ở mức độ trừu tượng hơn so với những 
thay đổi. Có nghĩa là `git add` có nhu cầu được gọi mỗi khi bạn thay đổi một 
tập tin (điều này liên quan đến việc git không "nhìn" tập tin theo tên và vị 
trí, mà theo mã băm của tập tin đó, có nghĩa là khi tập tin bị sửa đổi, đối với
Git, đó hoàn toàn là một tập tin khác). Nghe có vẻ "phiền hà", nhưng điều này 
tỏ ra hữu hiệu trong việc giữ ngăn nắp một dự án.

**Vùng Trạng thái**

Vùng Trạng thái (Stagin Area) là một trong những tính năng độc đáo của Git, và 
nó có thể làm mất của bạn một cơ số thời gian để thấm được nếu bạn là người 
đến từ nền tảng SVN (hoặc thậm chí là Mercurial). Về bản chất nó giống như là 
một bộ đệm nằm giữa thư mục hiện hành và phần lịch sử dự án.

Thay vì cam kết tất cả các thay đổi mà bạn đã thực hiện kể từ lần cam kết cuối 
cùng, Trạng thái cho phép bạn nhóm những thay đổi có liên quan tới nhau vào một
ảnh chụp được ưu tiên quan sát kỹ trước khi bạn thực sự cam kết nó vào lịch sử 
dự án. Điều này có nghĩa là bạn có thể làm tất cả các thể loại chỉnh sửa với 
những tập tin khác nhau, và sau đó chia chúng ra thành các cam kết nhỏ hơn một 
cách hợp lý, và cam kết từng mảnh một. Trong bất kỳ một hệ thống quản lý phiên 
bản nào, việc tách những cam kết thành các cam kết nhỏ (và cô đặc tới mức mỗi 
cam kết chỉ ám chỉ một thay đổi có ý nghĩa) luôn rất quan trọng vì nó giúp cho 
sự dễ dàng trong việc theo dõi lỗi và phục hồi những thay đổi mà không làm ảnh 
hưởng đến những thành phần khác của dự án.** 

#####Ví dụ

Khi bạn bắt đầu một dự án, `git add` cung cấp chức năng tương tự như 
`svn import`. Để khởi tạo một cam kết cho thư mục hiện tại, sử dụng hai câu 
lệnh sau đây:

    git add .
    git commit

Khi dự án đã bắt đầu chạy, những tập tin mới có thể được thêm vào bằng cách 
cung cấp đường dẫn cho lệnh `git add`:

    git add hello.java
    git commit

Câu lệnh đầu tiên cũng được dùng để ghi lại thay đổi của một file đã tồn tại 
(trong trường hợp này là file hello.java). Nhắc lại, Git không theo dõi sự 
thay đổi trạng thái của file mới giống như file mà đã được thêm vào kho bằng 
lệnh `git add`.

####Lệnh `git commit`





































































