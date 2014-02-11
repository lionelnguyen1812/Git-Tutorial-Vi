[link_gitbare]: http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/vi/ch03.html
[link_spec_ranges_ref]: https://www.kernel.org/pub/software/scm/git/docs/gitrevisions.html

Hướng dẫn sử dụng Git cho dự án Agile
=====================================

# Chơi với Git đi

![](/images/git_home.png)

Nhiều nhóm phát triển phần mềm đã chuyển đổi từ những hệ thống quản lý mã 
nguồn tập trung như Subversion sang hệ thống phân tán giống Git.

Loạt bài viết này nhằm mục đích giới thiệu một cái nhìn về hệ thống Git, 
những mã lệnh của nó cùng với guides để sử dụng trong thực tế. Nhóm của bạn 
hoàn toàn có thể giữ nguyên phong cách làm việc của mình trong khi vẫn có 
được những lợi ích từ sự nhẹ nhàng và nhiều tính năng mà Git mang tới.

# Hướng dẫn Git

![](/images/git_tutorials.png)

## 1. Git Cơ bản

![](/images/git-tutorial_basics.png)

Loạt bài đầu tiên - "Git cơ bản" cung cấp khái quát ngắn gọn về những mã lệnh 
điều khiển quan trọng nhất của Git. Đầu tiên, section *Cài đặt một repo* 
giải thích tất cả những công cụ cần thiết để bạn có thể bắt đầu một dự án 
quản lý mã nguồn. Sau đó thì, section còn lại giới thiệu những lệnh điều 
khiển mà bạn sẽ thường xuyên sử dụng.

Đi theo tới phần cuối của chương này, bạn đã có thể tạo được một kho Git, 
ghi một bản chụp nhanh của project của bạn cho mục đích an toàn, và xem lịch 
sử sửa đổi của project của bạn.

### Khởi tạo một kho Git

#### Lời người dịch

Trong bản dịch này, từ "kho" tương ứng với "repository" trong bản gốc tiếng 
Anh.

Tài liệu này có một số nội dung mà giải thích rõ hơn cho các độc giả mà đã 
quen thuộc với một trình quản lý phiên bản khác nào đó như SVN hoặc VCS. Nhưng 
điều này không có nghĩa là tài liệu này là khó tiếp cận đối với người mới.

Dịch vụ lưu trữ kho Git lớn nhất hiện nay là **GitHub** cung cấp cho bạn một 
client Git với giao diện đồ họa rất đẹp và dễ dùng. Nhưng chỉ có trên Windows, 
dù thế tôi vẫn khuyến khích bạn tốt nhất sử dụng cơ chế dòng lệnh vì chỉ ở 
trên một terminal bạn mới có thể quan sát được điều gì đang thực sự xảy ra một 
cách chi tiết nhất (thực tế, cá nhân tôi còn luôn có cảm giác bất an khi nhấn 
nút **Sync** trên giao diện trình điều khiển đồ họa được cung cấp bởi 
**GitHub**.

Để sử dụng được mã lệnh tốt, bạn nên trang bị cho mình một chút về các command 
cơ bản như `dir`, `cd`, `cd ..`, `cd \`, `md`, ... (trên cmd của Windows) hay 
`ls`, `mkdir`, `cd`, `rm`,... trên các hệ điều hành họ Unix/Linux.*

#### Lệnh `git init`

![](/images/git-tutorial-basics-init.png)

Lệnh `git init` sẽ tạo một kho Git mới trên thư mục hiện tại. Nó có thể dùng 
để chuyển một project chưa được cung cấp sự quản lý phiên bản thành một bản 
chính Git hoặc tạo ra một kho Git rỗng mới.

**Phần lớn các lệnh Git khác không cho phép chạy bên ngoài thư mục repo** 
(bản thân "repo" là một thư mục, nên tôi không viết là "thư mục chứa repo"). 
Vì vậy gần như đây luôn là lệnh Git đầu tiên bạn thực hiện trên một project 
mới.

Chạy `git init` sẽ tạo ra một thư mục ẩn `.git` chứa các file metadata trong 
thư mục hiện hành. Ngoại trừ thư mục `.git`, những phần còn lại của
project sẽ không có gì thay đổi (không giống như SVN yêu cầu phải có một thư
mục metadata trong mỗi thư mục con).

##### Sử dụng

    git init

Chuyển thư mục hiện thành thành một kho Git. Hành động này tạo một thư 
mục ẩn `.git` vào thư mục hiện hành. Sau khi khởi tạo, kho ngay lập tức
sẵn sàng cho việc theo dõi các sửa đổi.

    git init <tên thư mục>

Tạo một thư mục với tên là <tên thư mục>, chuyển thư mục đó thành một bản 
chính Git, thư mục này sẽ chỉ chứa thư mục ẩn `.git`.

    git init --bare [<tên thư mục>]

khởi tạo một kho thuần. Tôi sẽ giải thích rõ hơn về kho thuần ngay sau đây.

##### Lời bàn

Khi so sánh với SVN, lệnh `git init` quá sức đơn giản cho việc khởi tạo một 
repo mới. Git không hỏi gì thêm, không cần import file, không checkout đủ thứ.
Tất cả những gì cần làm là `cd` tới thư mục project và chạy `git init`. Sau đó
bạn đã có một kho Git với tất cả các chức năng mà hệ thống Git mang lại.

Dù sao, trong đa số project, `git init` chỉ cần chạy một lần để tạo repository 
trung tâm, những cộng tác viên khác không cần phải chạy `init` cho kho ở phía
máy tính của họ. Thay vì đấy, họ sẽ dùng `git clone` để tạo một bản sao về máy 
tính của mình.

##### Repo thuần

Gọi như vậy vì nó không chứa thư mục làm việc (tôi có tham khảo 
giải nghĩa này từ một bài dịch khác của tác giả Trần Ngọc Quân, các bạn có thể
xem bài viết gốc [ở đây][link_gitbare]). Nó chỉ chứa các tệp tin trong thư mục 
`.git`. Hay nói cách khác nó chứa lịch sử mã nguồn của một dự án, và không bao
giờ giữ các tập tin của bất kỳ phiên bản nào.

Kho thuần đóng vai trò hoạt động giống như máy chủ trung tâm trong SVN. Những 
sự biên soạn mã nguồn chỉ xảy ra trên những bản sao, vì thế thư mục chủ ở máy 
chủ trung tâm có thể hoạt động mà không cần thư mục làm việc. Điều này có nghĩa
là khi mô hình hóa luồng làm việc trên Git, ta có kho trung tâm sẽ là 
kho-thuần, trong khi những kho địa phương trên máy của các cộng tác viên thì 
không.

![](/images/git-tutorial-basics-init-barrepositories.png)

##### Ví dụ

Nếu việc xuất hiện khái niệm kho thuần làm bạn lo ngại, thì rất may là, việc 
khởi tạo kho thuần thường được dịch vụ lưu trữ kho Git mà bạn dùng thực hiện 
tự động. Mà GitHub là một ví dụ. Trong một trường hợp khác nào đó, quá 
trình tạo kho thuần vào máy chủ trung tâm trông sẽ giống như dưới đây

    ssh @
    cd path/above/repo
    git init --bare my-project.git

Câu lệnh đầu tiên sẽ SSH vào máy chủ sẽ chứa kho git trung tâm. Sau đó bạn `cd` 
thư mục chứa project. Và câu lệnh cuối cùng sử dùng cờ `--bare` để tạo một kho
thuần. Những cộng tác viên sau đó đã có thể dùng lệnh `git clone my-project.git`
để tạo một bản sao địa phương trên máy tính của họ.

#### Lệnh `git clone`

![](/images/git-tutorial-basics-clone.png)

Lệnh `git clone` giúp nhân bản một kho Git đã được init. Hành động này trông 
tương tự với `svn checkout`, nhưng tôi có thể giải thích rõ hơn ở đây, bạn hãy 
nghĩ về sự khác nhau giữa "nhân bản" với "lấy về nội dung". Với Git, bản sao 
lấy về giống y hệt bản sao ở máy chủ trung tâm. Tất cả những gì có thể làm được
trên bản chính thì cũng có thể làm với bản sao. Bản sao cũng có mọi thứ của kho
chính, có lịch sử sửa đổi của riêng nó, bạn có thể quản lý mã nguồn với riêng 
nó, hoàn toàn biệt lập với kho chính.

Như một tiện ích, việc clone sẽ tự động tạo ra một thứ gọi là "nguồn gốc" 
(nguyên bản: origin), thứ này chỉ trở lại kho gốc. Sự tồn tại của "nguồn gốc" 
giúp Git dễ dàng tương tác với kho trung tâm và hoàn thiện sự "giống một cách 
hoàn hảo" của bản sao so với bản chính.

##### Sử dụng

    git clone <repo>

Nhân bản một kho Git tồn tại ở địa chỉ `<repo>` vào thư mục hiện hành. Kho gốc 
có thể tồn tại trên hệ thống địa phương hoặc trên máy chủ từ xa mà được truy 
cập thông qua giao thức HTTP hoặc SSH.

    git clone <repo> <derectory>

Nhân bản kho Git <repo> tới thư mục <directory> ở máy địa phương.

#####Lời bàn

Nếu một project đã được cài đặt vào máy chủ trung tâm, lệnh `git clone` là 
cách thông dụng nhất để tạo bản sao. Giống như `git init`, nhân bản thường chỉ 
cần làm một lần vào lúc cộng tác viên yêu cầu cần có bản sao, sau đó mọi hành 
động quản lý phiên bản và cộng tác sẽ được quản lý trên kho địa phương của họ.

#####Cộng tác trực tiếp Từ-Kho-Đến-Kho

Một điểm rất quan trọng cần phải hiểu rõ đó là ý tưởng về "bản sao" của Git 
rất khác so với bản sao được checkout về từ kho SVN. Không giống SVN, Git 
không có sự khác biệt nào giữa bản sao hiện hành (là bản sao ở phía các cộng 
tác viên) và bản chính ở kho trung tâm - như tôi đã nhấn mạnh ở phần trước, 
tất cả những gì thực hiện được với kho trung tâm thì cũng làm được trên bản 
sao.

Sự khác biệt này khiến cho làm việc cộng tác với Git về cơ bản khác hoàn toàn 
khi so với SVN. Trong khi SVN phụ thuộc vào mối liên hệ giữa bản sao và kho 
trung tâm, sự cộng tác ở Git dựa trên sự ảnh hưởng của từng kho (hay là từng 
bản sao (hay cũng có thể gọi là bản chính?)) với nhau. Thay vì kiểm tra bản 
sao hiện hành vào kho chính SVN, ở Git bạn `push` hoặc `pull` những `commit` 
từ một kho này tới một kho khác.

![](/images/git-tutorial-basics-clone-repotorepocollaboration.png)

Dĩ nhiên, không có điều gì cản trở bạn chỉ dùng mỗi một kho Git duy nhất để 
đồng bộ. Ví dụ như, bằng việc đơn giản là thiết kế một kho Git nào đó như là 
kho "trung tâm", sẽ cho phép nhóm của bạn triển khai mô hình "Luồng làm việc 
với kho trung tâm" - có điều là, điểm này, dùng Git, và hoàn toàn bằng các quy 
ước chứ không phải là "bắt buộc phải làm thế" giống như khi sử dụng VCS.

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

![](/images/git-tutorial-basics-config.png)

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

#####Lời bàn

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

###Ghi lại những ảnh chụp

####Lệnh `git add`

![](/images/git-tutorial-basics-add.png)

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

#####Lời bàn

Lệnh `git add` và `git commit` tạo nên cơ sở cho luồng làm việc trên Git. Chúng
là hai lệnh và bất cứ người dùng Git nào cũng cần phải nắm vững, bất kể mô hình
cộng tác của team bạn ra sao. Chúng là những phương tiện để ghi lại các phiên 
bản của một project vào lịch sử của kho. 

Phát triển một dự án luôn xoay quanh các mô hình chỉnh sửa, giai đoạn và commit
cơ bản. Trước tiên, bạn chỉnh sửa các tệp tin trong thư mục hiện hành. Khi bạn
đã sẵn sàng để lưu một bản sao của trạng thái hiện tại của dự án, bạn đưa thay 
đổi đó lên mức độ "đã chấp nhận" bằng lệnh `git add`. Sau khi bạn đã cảm thấy 
OK với trạng thái hiện giờ của phiên bản, bạn commit nó vào lịch sử dự án với 
lệnh `git commit`. 

![](/images/git-tutorial-basics-add-addsnapshot.png)

Lệnh `git add` không tương đồng với `svn add` (cái mà ngay lập tức thêm tập tin
vào kho). Thay vào đó, `git add` làm việc ở mức độ trừu tượng hơn so với những 
thay đổi. Có nghĩa là `git add` có nhu cầu được gọi mỗi khi bạn thay đổi một 
tập tin (điều này liên quan đến việc git không "nhìn" tập tin theo tên và vị 
trí, mà theo mã băm của tập tin đó, có nghĩa là khi tập tin bị sửa đổi, đối với
Git, đó hoàn toàn là một tập tin khác). Nghe có vẻ "phiền hà", nhưng điều này 
tỏ ra hữu hiệu trong việc giữ ngăn nắp một dự án.

**Vùng Trạm**

Vùng Trạm (Stagin Area) là một trong những tính năng độc đáo của Git, và 
nó có thể làm mất của bạn một cơ số thời gian để thấm được nếu bạn là người 
đến từ nền tảng SVN (hoặc thậm chí là Mercurial). Về bản chất nó giống như là 
một bộ đệm nằm giữa thư mục hiện hành và phần lịch sử dự án.

Thay vì commit tất cả các thay đổi mà bạn đã thực hiện kể từ lần commit cuối 
cùng, Trạng thái cho phép bạn nhóm những thay đổi có liên quan tới nhau vào một
ảnh chụp được ưu tiên quan sát kỹ trước khi bạn thực sự commit nó vào lịch sử 
dự án. Điều này có nghĩa là bạn có thể làm tất cả các thể loại chỉnh sửa với 
những tập tin khác nhau, và sau đó chia chúng ra thành các commit nhỏ hơn một 
cách hợp lý, và commit từng mảnh một. Trong bất kỳ một hệ thống quản lý phiên 
bản nào, việc tách những commit thành các commit nhỏ (và cô đặc tới mức mỗi 
commit chỉ ám chỉ một thay đổi có ý nghĩa) luôn rất quan trọng vì nó giúp cho 
sự dễ dàng trong việc theo dõi lỗi và phục hồi những thay đổi mà không làm ảnh 
hưởng đến những thành phần khác của dự án.** 

#####Ví dụ

Khi bạn bắt đầu một dự án, `git add` cung cấp chức năng tương tự như 
`svn import`. Để khởi tạo một commit cho thư mục hiện tại, sử dụng hai câu 
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

![](/images/git-tutorial-basics-commit.png)

Lệnh `git commit` sẽ commit ảnh chụp đã được đưa vào Vùng Trạm vào lịch 
sử dự án. Ảnh chụp đã được commit có thể coi như một phiên bản "an toàn" của dự
án - Git sẽ không bao giờ thay đổi gì ở đó trừ khi bạn dứt khoát yêu cầu. Cùng 
với `git add`, đây là một trong những lệnh quan trong nhất của Git.

Tuy có tên giống nhau, nhưng `commit` của Git không giống như `svn commit`. Ở 
Git, ảnh chụp chỉ được commit vào kho địa phương, và việc `commit` hoàn toàn 
không tạo nên tương tác gì với các kho ở những nơi khác.

#####Sử dụng

    git commit

Commit ảnh đang được lưu trong Vùng Trạm. Hành động này sẽ mở ra 
text-editor để bạn nhập vào "commit message". Sau khi bạn đã nhập mô tả về 
commit vào đó, hãy lưu lại và đóng text-editor, tới lúc đó việc commit mới thực
sự hoàn thành.

    git commit -m "<message>"

Commit ảnh đang được lưu trong Vùng Trạm, nhưng thay vì mở text-editor 
sau đó, bạn nhập mô tả commit vào <message>.

    git commit -a

Commit ảnh của tất cả những thay đổi trên thư mục hiện hành. Có nghĩa là
nó commit tất cả những thay đổi của những file mà đã được "track" trước đó 
bằng lệnh `git add`. Việc này giống như bạn dùng `git add <file>` để add tất cả
những file vừa bị thay đổi vào Vùng Trạm, sau đó chạy `git commit`.

#####Lời bàn

"Ảnh chụp luôn luôn được commit vào kho địa phương". Đây là sự khác nhau cơ bản
khi so sánh về commit của Git với SVN - nơi mà bản sao hiện hành được commit 
trực tiếp vào kho trung tâm. Ngược lại, Git không yêu cầu bạn phải tương tác 
với kho trung tâm cho tới khi bạn đã sẵn sàng. Cũng như Vùng Trạm là bộ đệm 
thư mục hiện hành và lịch sử dự án, kho địa phương của mỗi cộng tác viên là một
bộ đếm giữa sự cộng tác của họ và kho trung tâm.

Điều này thay đổi mô hình phát triển dự án cơ bản của người dùng Git. Thay vì 
làm một sự thay đổi vào commit nó trực tiếp tới kho trung tâm, những cộng tác 
viên có cơ hội tích lũy các commit nhỏ và tách biệt về mặt ý nghĩa trong kho 
địa phương của họ. Việc này có nhiều lợi thế hơn so với phong cách hợp tác của 
SVN: sẽ dễ dàng hơn để chia từng sự thay đổi vào từng commit cô đặc, giữ những 
thay đổi có cùng nhóm ý nghĩa vào với nhau trong một commit, và giữ cho lịch sử
ở kho địa phương được sạch sẽ trước khi xuất bản nó vào kho trung tâm. Nó cũng 
cho phép các cộng tác viên làm việc trong một môi trường hoàn toàn cô lập và có
thể từ chối hội nhập (với các kho khác) cho đến khi họ đạt đế một điểm break 
tốt nhất.

**Chỉ chấp nhận ảnh chụp, không trình bày nhiều!**

Bên cạnh sự khác biệt về triết lý giữa Git và SVN, sự triển khai cơ bản của 
chúng cũng được thiết kế hoàn toàn khác nhau. Trong khi SVN theo dõi sự khác 
biệt của một tập tin, mô hình quản lý phiên bản Git được dựa trên các ảnh chụp.
Ví dụ, một commit SVN chỉ ghi lại các thay đổi của một file so với file gốc. 
Git, khác vậy, nó ghi lại toàn bộ nội dung của mỗi tập tin trong tất cả các 
commit. Nhắc lại, đối với Git không tồn tại khái niệm "đây là file abc và nó đã
được thay đổi thành như thế này", với Git, "đây là file abc ở đây, lúc nãy cũng
có một file abc ở đây, nó là 2 file khác nhau".

![](/images/git-tutorial-basics-commit-snapshots.png)

Điều này làm cho nhiều hoạt động Git nhanh hơn nhiều so với SVN, bởi vì bất cứ
một phiên bản nào của một tập tin cũng không phải là một sự "lắp ráp" từ những 
ghi chú về quá trình thay đổi của nó so với bản gốc. Phiên bản hoàn chỉnh của 
tập tin đã có sẵn, tồn tại thật, và sẵn sàng truy cập ngay từ cơ sở dữ liệu nội
bộ của Git.

Mô hình ảnh chụp của Git có tác động sâu sắc đến hầy như mọi khía cạnh của Mô 
hình Quản lý Phiên bản của nó, ảnh hưởng đến tất cả mọi thứ, từ sự phân nhánh 
đến gộp nhánh đến luồng làm việc cộng tác của nó.

#####Ví dụ

Ví dụ theo sau đây giả định rằng bạn đã chỉnh sửa một số nội dung trong tập tin
hello.java và đã sẵn sàng để commit nó vào lịch sử của dự án. Trước tiên bạn 
cần phải cho "lên sàn" tập tin mới bằng `git add`, sau đó bạn mới có thể commit
ảnh chụp đã được "lên trạm".

    git add hello.java
    git commit

Lệnh cuối cùng sẽ mở ra một text-editor (cái nào thì đã được định trước ở phần 
`git config`) hỏi bạn về mô tả commit, cùng với đó là một danh sách những gì 
đang được commit, trông nó như sau:

    # Please enter the commit message for your changes. Lines starting
    # with '#' will be ignored, and an empty message aborts the commit.
    # On branch master
    # Changes to be committed:
    # (use "git reset HEAD ..." to unstage)
    #
    # modified: hello.py
    #

Git không yêu cầu mô tả commit phải tuân theo bất cứ một ràng buộc cú pháp nào,
nhưng định dạng kinh điển là tóm tắt toàn bộ nội dung commit vào dòng đầu tiên 
trong ít hơn 50 ký tự, để ra một dòng trống, sau đó giải thích chi tiết về 
những gì đang được thay đổi. Ví dụ:

    Sửa nội dung thông báo ra của class Hello
    
    - Cập nhật hàm sayHello() để thông báo ra username
    - Sửa hàm sayGoodbye() để hiện ra thông báo thân thiện hơn

Lưu ý rằng nhiều nhà phát triển thích dùng thì hiện tại trong mô tả commit của 
họ. Bởi vì việc đó giúp họ có thể đọc mô tả giống như hành động xảy ra trên kho
lưu trữ, một lợi ích mà có thể làm cho rất nhiều các hoạt động soát lại lịch sử
trở nên trực quan hơn.

###Kiểm tra một kho Git

####Lệnh `git status`

![](/images/git-tutorial-basics-status.png)

Lệnh `git status` sẽ giúp hiển thị trạng thái của thư mục hiện hành và Vùng 
Trạm. Nó cho bạn thấy những thay đổi nào đã lên sàn, những nào chưa, và tập tin
nào chưa được theo dõi bởi Git. Lệnh `git status` sẽ không cho bạn thấy bất kỳ 
thông tin nào liên quan đến lịch sử dự án đã commit. Nếu cần thứ đó, bạn cần sử
dụng `git log`.

#####Sử dụng

    git status

Hiển thị những tập tin đã lên sàn, chưa lên sàn, và chưa được theo dõi.

#####Lời bàn

Lệnh `git status` thực sự tương đối đơn giản. Nó cho bạn thấy những gì đã xảy 
ra với `git add` và `git commit`. Thông báo cũng bao gồm những hướng dẫn có 
để cho lên sàn và gỡ xuống những tập tin. Thông thường lệnh này sẽ cho ra ba 
mục nội dung chính trông giống như dưới đây:

    # On branch master
    # Changes to be committed:
    # (use "git reset HEAD ..." to unstage)
    #
    # modified: hello.java
    #
    # Changes not staged for commit:
    # (use "git add ..." to update what will be committed)
    # (use "git checkout -- ..." to discard changes in working directory)
    #
    # modified: main.java
    #
    # Untracked files:
    # (use "git add ..." to include in what will be committed)
    #
    # hello.class

**Bỏ qua tập tin**

Việc các tập tin không được theo dõi thường rơi vào hai loại. Chúng đã hoặc vừa
mới thêm vào dự án nhưng chưa được thêm vào (bằng `git add`), hoặc chúng được 
sinh ra bởi những trình dịch như những file `.pyc`, `.obj`, `.exe`, v.v.. Trong
khi loại đầu tiên được liệt kê trong `git status` là một ưu điểm chắc chắn, 
nhưng loại sau lại làm cho `git status` đăng ra những thứ không thật sự thể 
hiện điều gì đang xảy ra với kho của bạn.

Vì lý do này, Git cho phép bạn hoàn toàn bỏ qua một số tập tin bằng cách đặt 
đường dẫn của chúng vào trong một file đặc biệt là `.gitignore`. Bất kỳ tập tin
nào bạn muốn liệt kê trong file này nên được để trên một dòng riêng biệt, và 
các ký hiệu `*` có thể được sử dụng như một ksy tự đại diện. Ví dụ, thêm dòng 
sau vào tập tin `.gitignore` trong thư mục gốc dự án của bạn sẽ ngăn chặn các 
file sinh ra do trình dịch javac tạo ra trong quá trình thực thi:

    *.class

**Ví dụ mẫu**

Sẽ là một thói quen tốt khi luôn kiểm tra trạng thái kho của bạn trướ khi 
commit những thay đổi để chắc chắn không vô tình phạm phải một lỗi nào đó mà 
bạn không cố ý. Ví dụ sau hiển thị trạng thái của kho lưu trữ trước và sau khi 
lên sàn và commit một ảnh chụp:

    # Edit hello.py
    git status
    # hello.py is listed under "Changes not staged for commit"
    git add hello.py
    git status
    # hello.py is listed under "Changes to be committed"
    git commit
    git status
    # nothing to commit (working directory clean)

Thông tin xuất ra đầu tiên sẽ hiển thị rằng có một vài tập tin chưa lên sàn. Kết
quả của hành động `git add` sẽ được phản ánh qua yêu cầu xem status thứ hai, và
lệnh`git status` cuối cùng sẽ cho bạn biết rằng không còn gì để commit - thư 
mục hiện hành hoàn toàn trùng khớp với ảnh chụp gần đây nhất. Một vài lệnh Git
(ví dụ như `git merge`) yêu cầu thư mục hiện hành phải sạch để bạn không vô 
tình ghi đè lên một thay đổi nào đó.

####Lệnh `git log`

![](/images/git-tutorial-basics-log.png)

Lệnh `git log` hiển thị danh sách những ảnh chụp đã được commit. Nó cho phép 
bạn liệt kê lịch sử dự án, lọc và tìm kiếm những thay đổi cụ thể. Trong khi 
`git status` cho phép bạn kiểm tra thư mục hiện hành và khu vực Vùng Trạm, thì 
`git log` chỉ hoạt động trên những lịch sử đã commit. Hãy xem kỹ ý nghĩa của 
hình minh họa dưới đây.

![](/images/git-tutorial-basics-logcommand.png)

Đầu ra của `git log` có thể được tùy biến theo nhiều cách từ việc lọc đơn giản 
những commit tới việc hiển thị chúng theo một định dạng hoàn toàn do người dùng
định nghĩa. Một số cấu hình phổ biến nhất của lệnh `git log` được trình bày 
trong phần dưới đây.

#####Sử dụng

    git log

Hiển thị toàn bộ lịch sử commit, theo format mặc định. Nếu đầu ra chiếm nhiều 
hơn một màn hình, bạn có thể dùng phím Space để cuộn và nhấn `q` để thoát.

    git log -n <limit>

Hiển thị danh sách <limit> lần commit cuối cùng. Ví dụ `git log -n 3` sẽ chỉ 
hiển thị 3 lần commit gần đây nhất.

    git log --oneline

Mô tả ngắn gọn mỗi commit trên một dòng đơn. Cờ này rất hữu ích khi ta cần một 
cái nhìn tổng quan vào lịch sử của dự án.

    git log --stat

Hiển thị thông tin như `git log` bình thường, nhưng bổ sung danh sách các tập 
tin được thay đổi và sô lượng tương đối của số dòng được thêm vào hoặc xóa đi 
của mỗi commit.

    git log -p

Hiển thị những bản vá đại diện cho mỗi commit. Hành động này cho thấy sự khác 
nhau đầy đủ của từng commit, đây là bản thông tin chi tiết nhất bạn có thể có
trong lịch sử dự án của bạn.

    git log --author="<pattern>"

Chỉ liệt kê những commit từ một tác giả cụ thể. Chuỗi <pattern> có thể là một 
chuỗi ký tự thuần túy hoặc một biểu thức đại diện.

    git log --grep="<pattern>"

Chỉ liệt kê những commit mà có mô tả commit phù hợp với <pattern>. <pattern> có
thể là chuỗi ký tự thuần túy hoặc là một biểu thức đại diện.

    git log <since>..<until>

Chỉ liệt kê những commit xảy ra giữa <since> và <until>. Cả hai tham số này có 
thể là ID của một commit nào đó, tên một nhánh nào đó, và một vài kiểu dữ liệu
khác mà bạn có thể tra cứu thêm [ở đây][link_spec_ranges_ref].

    git log <file>

Chỉ liệt kê những commit mà có sự tham gia của tập tin <file>. Đây là cách dễ 
nhất để xem lịch sử của một tập tin cụ thể.

    git log --graph --decorate --oneline

Một vài lựa chọn hữu ích khác mà bạn có thể xem xét. Cờ `--graph` sẽ vẽ một 
biểu đồ (bằng ký tự) ở phía bên tay trái của mô tả commit. Cờ `--decorate` sẽ 
thêm tên của các nhánh hoặc các thẻ của các commit được hiển thị. Cờ 
`--oneline` hiển thị thông tin trên chỉ một dòng đơn hỗ trợ việc duyệt qua rất 
nhiều commit trong nháy mắt.

#####Lời bàn

Lệnh `git log` là công cụ cơ bản để thăm dò lịch sử của một kho Git. Nó là lệnh
bạn dùng khi cần tìm một phiên bản cụ thể của một dự án, tìm ra những thay đổi 
sẽ được đưa vào kết hợp với một tính năng của nhánh nào đó, hoặc xem danh sách 
những cộng tác viên đang trễ tiến độ.

    commit 3157ee3718e180a9476bf2e5cab8e3f1e78a73b7
    Author: John Smith

Đa số những tác vụ đó khá dễ thực hiện; dù sao, dòng đầu tiên đã đảm bảo được
một vài chứng minh. Chuỗi 40 ký tự sau từ "commit" là một mã hash SHA-1 của nội 
dung commit. Chuỗi này phục vụ hai mục đích. Đầu tiên, nó đảm bảo tín toàn vẹn 
của các commit, nếu nó bị hỏng, nó sẽ tạo ra một mã hash hoàn toàn khác. Thứ 
hai, nó phục vụ như là một ID duy nhất cho các commit.

ID này có thể được sử dụng trong những lệnh như `git log <since>..<until>` để 
đề cập đến những commit cụ thể. Ví dụ `git log 3151e..5ab91` sẽ hiển thị mọi 
thứ giữa 2 commit có ID bắt đầu bằng 3151e và 5ab91. Bên cạnh mã hash, tên 
nhánh (sẽ được trình bày kỹ hơn trong phần *Nhánh Git*) và từ khóa `HEAD` là 
một vài cách phổ biến khác để để cập tới những commit riêng biệt. `HEAD` luôn 
đề cập tới commit hiện tại, do đó có thể coi nó như một nhánh hoặc một commit
cụ thể.

Ký tự `~` rất hữu ích cho việc tham chiếu tương đối tới node chả của một 
commit. Ví dụ `3151e~1` để cập tới commit xảy ra ngay trước 3151e, và `HEAD~3` 
là một cách tuyệt vời để chỉ tới commit nằm trước commit hiện tại 3 cấp.

Ý tưởng đằng sau tất cả những phương pháp nhận dạng là để cho bạn thực hiện 
hành động dựa trên những commit cụ thể. Và lệnh `git log` thường là điểm khởi 
đầu cho những tương tác này, vì nó cho phép bạn tìm thấy những commit mà bạn 
muốn làm việc với.

#####Ví dụ mẫu

Phần *Usage* ở trên đã cung cấp nhiều ví dụ sử dụng `git log`, nhưng hãy nhớ 
rằng một số tùy chọn khác nhau có thể được kết hợp thành một lệnh duy nhất.

    git log --author="John Smith" -p hello.java

Lệnh này sẽ hiển thị toàn bộ sự thay đổi được mà John Smith đã thực hiện với 
tập tin `hello.java`.

Cú pháp `..` rất hữu dụng để so sánh các nhánh với nhau. Ví dụ sau đây hiển thị
một tổng qua về tất cả các commit mà đã được nhận bởi nhánh `some-feature` 
nhưng không có trong nhánh `master`.

    git log --oneline master..some-feature

##2. Hoàn tác

![](/images/git-tutorial_undoing-changes.png)

###Xem lại những commit cũ

####Lệnh `git checkout`

![](/images/git-training-undoing-changes.png)

###Hoàn tác những thay đổi chia sẻ

####Lệnh `git revert`

![](/images/git-tutorial_changes-revert.png)

###Hoàn tác những thay đổi địa phương

####Lệnh `git reset`

![](/images/git-tutorial-changes-reset.png)

####Lệnh `git clean`

![](/images/git-tutorial-changes-clean.png)

##3. Nhánh Git

![](/images/git-tutorial_branching-merging.png)

####Lệnh `git branch`

![](/images/git-tutorial_branching.png)

####Lệnh `git checkout`

![](/images/git-tutorial_branching-checkout.png)

####Lệnh `git merge`

![](/images/git-tutorial_branching-merge.png)

##4. Viết lại lịch sử Git

![](/images/git-tutorial_rewriting-history.png)

####Lệnh `git commit --amend`

![](/images/git-tutorial-commit-amend.png)

####Lệnh `git rebase`

![](/images/git-tutorial_history-rebase.png)

####Lệnh `git rebase -i`

![](/images/git-tutorial_history-rebase-i.png)

##5. Kho Git từ xa

![](/images/git-tutorial-remote-repos.png)

####Lệnh `git remote`

![](/images/git-tutorial-remote.png)

####Lệnh `git fetch`

![](/images/git-tutorial-remote-repositories-fetch.png)

####Lệnh `git pull`

![](/images/git-tutorial-remote-repositories-pull.png)

####Lệnh `git push`

![](/images/git-tutorial-remote-repositories-push.png)

#Luồng làm việc Git


