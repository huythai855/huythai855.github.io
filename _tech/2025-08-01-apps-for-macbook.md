---
layout: post
title: "Những app mình dùng cho Macbook"
subtitle: "Cập nhật đến T8/2025"
date: 2025-08-01 00:00:00 -0400
background: '/img/bg-index.png'
---

Hehe, nhân một ngày vẫn đang ở Hàn Quốc 🇰🇷, vì là cuối tuần, mai đi chơi, lười học quá nên mình kiếm việc gì đó khác để làm. Thấy cũng lâu chưa cập nhật blog rùi nên muốn viết một bài chơi chơi (thực ra đã listing nhiều topic lắm nhưng chưa có hứng và có thời gian viết, hiuhiu).


Mình dùng Macbook cũng đã được hơn một năm rùi, từ ngày mới vào FPT được khoảng 1 tháng (chắc đầu tháng 6/2024), máy mình dùng là **Macbook Pro M3 16/512GB**, thời điểm mua thì dòng M3 cũng đang là chip mới nhất, mấy tháng sau đó ra M4 thì phải, thấy dân tình bảo giá bản cũ tụt như tụt quần luôn mà mình cũng không quan tâm lắm, vẫn thấy happy và thấy phục vụ được cho công việc của mình là được rùi.


**Note**: mặc dù là dân kỹ thuật, nhưng bài viết sẽ nêu những quan điểm đến từ trải nghiệm là chính, chứ mình cũng không đào sâu về các nguyên lý kỹ thuật (tại sao tốt, tại sao không tốt), vì mình cũng không đủ “trình” để phân tích kỹ, cũng như mọi người cũng chẳng cần quan tâm việc đó lắm. Nếu nó ngon, nó ngon, vậy thôi.

_________________________________________


## **Điểm thích và không thích khi dùng Macbook (với dân dev)**


Nào, vấn đề muôn thủa khi mọi người lần đầu tiên động vào Mac. *“Bỏ đi”, “Không tương thích đâu”, “Lỗi lắm”*,… mình nghĩ những lo ngại đấy chỉ dành cho những người chưa dùng macbook bao giờ hoặc dùng ở khoảng 5 năm trước, khi mới bắt đầu có Apple Silicon hoặc vẫn đang dùng chip Intel, còn giờ thì Macbook và cả Macbook dùng Apple Silicon đã quá phổ biến, dùng trong business nhiều và mình thấy gần như các app đều đã hỗ trợ rất tốt cho dòng máy này. Mình thấy gần như rất ít gặp tình trạng một app nào đó mình cần mà chỉ hỗ trợ cho Windows, Ubuntu mà không có trên Mac cả, hoặc là luôn tìm được những app tương tự thay thế, thậm chí là ngon hơn.


**Ưu điểm:**

- cùng một cấu hình (ví dụ 16GB RAM), cảm giác dùng Macbook luôn mượt hơn và có khả năng sử dụng tốt hơn so với một máy Windows, thậm chí là cả Ubuntu. Hồi còn làm công ty F, nhiều lúc code microservices, mình phải bật và chạy 4 cái Pycharm, chạy mấy image trong Docker, bật Lens, Postman và cả chục tab trình duyệt Edge để đọc docs, nghe youtube, messaging cùng một lúc mà vẫn sử dụng rất bình thường. Mình chưa từng thấy một máy nào Windows làm được điều tương tự, thậm chí mở đến chục tab trình duyệt là bắt đầu not responding rồi.
- Pin trâu, dù mình dùng như phá, nhưng giờ chạy workload tương đối vẫn thấy máy chạy được đến khoảng 8-10 tiếng, lúc mới mua thì còn đến khoảng 12 tiếng.
- Loa hay, ấm. Màn Liquid Retina đẹp, rất đẹp, hiển thị độ chân thực màu tốt, 120Hz, nhìn đã con mắt luôn, quay ra dùng máy công ty màn cùi thấy đui cả con mắt hiuhiu
- Hệ sinh thái Apple rất tốt, đồng bộ tốt với iphone, ipad trong các app/tính năng native như icloud, ảnh, airdrop, note, reminder, calendar, iphone mirroring cũng là một cái mình khá thích (ban đầu nghĩ là chẳng dùng làm gì, nhưng sau lại thấy tiện). Cũng có thời gian mình lấy ipad ra làm màn phụ cho macbook nữa. Nói chung dùng là nghiện, muốn sắp cả bộ macbook, iphone, ipad, apple watch liền :))
- Trông sang (cái này chắc tùy người, mình thấy bình thường) =)))


**Nhược điểm**

- Chip ARM: tiết kiệm năng lượng hơn, nhưng đôi khi sẽ không tương thích được với các hệ thống khác. Ví dụ: mình đóng Docker Image trên máy Mac (kiến trúc ARM) thì Image đó không chạy được trên các hệ thống khác như Windows, Linux (kiến trúc AMD) → tất nhiên sẽ không thể dùng cho server hay chạy trên k8s. Đọc đến đây nhiều người sẽ hỏi: wtf, m code trên remote server đi, code máy local làm gì xong kêu, thì mình sẽ trả lời là: vẫn có nhiều cái muốn thử local cho tiện mà, đóng image là một ví dụ, cần test nhiều thứ nữa, kể cả giao diện, hơn là chỉ có server. À, chưa kể vụ mấy thư viện kiểu tensorflow cũng không hỗ trợ tốt cho Apple Silicon,… muốn cài, chạy ổn định phải vọc vạch thêm.
- Giá “đắt”: thực ra mình không nghĩ đây là một nhược điểm gì lắm, tất nhiên, bạn luôn thấy giá Mac luôn đắt hơn máy thường với cùng “cấu hình”. Nhưng như mình đã nói ở phần trên, cùng cấu hình nhưng máy Mac luôn cho hiệu năng cao hơn, cũng như đủ thứ xịn xò nữa như: màn đẹp, loa hay, build tốt, pin trâu, hệ sinh thái tốt thì mình nghĩ nó không hề overprice chút nào. Chỉ khoảng hơn 20tr cho Air M4 (đời mới nhất, tháng 8/2025) và so với những công việc nó có thể hỗ trợ mình thì mình thấy đáng đến từng đồng.

<br />



Oke, phần trên lan man dài quá rồi, phần này mới vào nội dung chính =)))


## Trình duyệt - Microsoft Edge

Phải nhìn nhật một sự thật rằng, không phải phần mềm nào, kể cả VSCode, mà được dùng nhiều như trình duyệt, vì mình dùng nó gần như cho mọi mục đích: xem youtube, vào google meet, vào facebook, đọc docs, viết docs công ty, tra cứu, dùng AI,… nên đó mới là ứng dụng quan trọng nhất và cần tối ưu nhất của mỗi người chứ không phải vscode hay gì cả. Mình vẫn dùng Microsoft Edge từ ngày xưa, kể từ khi nó dùng nhân Chromium thì thấy khá ổn, còn tối ưu tốt, không nuốt ram như Chrome nữa. Tất cả dữ liệu của mình: bookmark, password,… đã dùng nhiều năm bên đó và cũng không muốn phải đồng bộ lại. 

Ngoài ra, giao diện của egde trên Windows và trên Mac cũng khá tương đồng, nên mình không mất nhiều thời gian làm quen lại từ đầu khi chuyển qua dùng Mac. Mình cũng thấy nhiều người dùng Mac dùng Safari, thấy cũng mượt, nhưng với mình, giao diện nó phù hợp để surfing vui vẻ, task nhẹ hơn là làm việc cả chục tab, lưu vài chục cái bookmark và sử dụng một cách hiệu quả cho công việc.

<br />

## Chụp màn hình - Lightshot Screenshot

Ủa, không phải chụp màn hình có sẵn với Mac rồi hả? À mình cũng công nhận điều đó, và thấy ảnh chụp bằng cái screen capture của mac cũng rất “nghệ thuật” (có viền blur). Nhưng khi đi làm công ty F thì mình thấy mọi người đều dùng Lightshot Screenshot, và thực sự nó rất tuyệt, nhất là khi cần trong công việc. Một số ưu điểm của app này mà app mặc định không có, có thể kể đến như: 

- Cap màn hình lưu vào clipboard luôn (không thấy app mặc định làm được, `Cmd+Shift+5` để mở app, chọn windows cần chụp, ấn vào để mở ảnh, chuột phải vào, ấn Copy, tắt cái ảnh đi (6 bước). Với Lightshot thì chỉ cần mở chụp ảnh (`Cmd+Shift+9`), chọn vùng cần chụp, ấn nút copy to clipboard (3 bước) → nhanh và tiện gấp đôi.
- Note chữ, khoanh tròn, highlight, mũi tên,… ngay trong ảnh chụp màn hình vô cùng đơn giản và nhanh. Khi chọn vùng chụp, ấn thêm 1-2 thao tác là được, phải gọi là siêu nhanh đặc biệt với dân tester, cần chụp evidence, highlight đoạn gửi cho đồng nghiệp, cho sếp,… cái này là điểm khác biệt mạnh mẽ nhất của Lightshot.
- Upload lên cloud, miễn phí. Thay vì gửi một cái ảnh to bự, nhiều khi cũng không tiện, vẫn từng bước như thế, bước cuối thay vì chọn save to clipboard, thì ấn nút upload, nó sẽ tự tạo 1 link → upload cho bạn → copy link đó vào clipboard để bạn sẵn sàng gửi đi đâu thì gửi, bạn cũng quản lý được các ảnh đã upload và không sợ mất đi đâu, thực sự là siêu tiện.

<br />

## Đọc PDF - Foxit Reader

Tìm app đọc PDF luôn là nỗi trăn trở của mình kể từ những ngày tháng dùng windows, cảm giác vẫn chưa có app nào đủ hết các yêu cầu của mình. Mình đã từng thử qua: trình đọc pdf của Chrome/Edge, Preview (mặc định của Mac), Foxit Reader (win, mac), gần đây có dùng qua PDF Gear. Và cuối cùng tìm ra điểm đến, có lẽ cuối cùng vẫn là Foxit Reader, chỉ vì một tính năng: shortcut: ấn phím `x` để vào chế độ comment, ấn phím `h` để về chế độ hand, ấn `z` để zoom, ấn `Cmd+Shift+I` để dùng bút, `Cmd+Shift+L` để kẻ đường,… → siêu tiện với mình, vì mình hay phải đọc slide khi nghe giảng và muốn note hết các ý quan trọng vào trong slide luôn. Thường thì mọi người giảng và lướt qua slide siêu nhanh, nếu cần di chuột lên thanh công cụ, ấn vào highlight, di chuột lại điểm mình cần, ấn,… một loạt thao tác mới bắt đầu note được thì rất chậm và không thể note kịp. Có một điểm trừ là mình note tiếng Việt bị lỗi font khá nhiều, thôi đành note tiếng Anh vậy, coi như luyện tập luôn :”>

<br />

## Cloud Storage - OneDrive

Mình dùng tài khoản trong gói Microsoft 365 Developer nên được free các ứng dụng Microsoft Office, ngoài ra OneDrive còn gần như không giới hạn, nên mình dùng luôn để sync data giữa các máy và để backup dữ liệu quan trọng nữa. Ngày xưa hồi cấp 3, mình hay dùng MEGA (cũng là một dạng cloud storage) để sync dữ liệu hàng ngày giữa máy ở trường và máy ở nhà. Gần như bạn code cái gì ở trường thì cứ để máy đấy, về nhà mở lap ra lại có tiếp, sửa tiếp, không cần git, không cần copy code và gửi qua messenger làm gì. Mình đã làm như thế hàng ngày liên tục trong suốt khoảng 2019-2021, cho tới khi hết cấp 3, lên đại học dùng 1 laptop cá nhân thôi nên cũng không còn nhu cầu vậy nữa. Thực ra giờ cũng không quá cần, nhưng chủ yếu mình sẽ dùng cho vụ backup dữ liệu, cũng như đi làm thì sync giữa máy ở nhà và máy ở cơ quan, cũng tiện.

<br />

## Sublime - Text Editor

Đơn giản, với dân kỹ thuật thì mình cần một cái gì đấy như notepad ở bên Windows (vì không phải lúc nào bạn cũng dùng vim hay cat file ra đọc được, nó tốt nhưng không tiện ở mọi trường hợp). Mình dùng Sublime từ khi dùng windows, nó tiện, nhẹ, đơn giản, free, cài theme được,… chỉ cần vậy thôi, còn Mac cũng có TextEditor mặc định nhưng nó cùi quá nên không dùng bao giờ.

<br />

## AI - ChatGPT

ChatGPT thì ai cũng dùng rồi, nhưng tại sao lại cần app trong khi chúng ta có web rồi. Mình thực ra cũng hay dùng web hơn, nhưng app cũng có cái tiện của nó, ví dụ: hiểu được context của một số app khác (ví dụ: vscode), bạn không cần phải copy tay vào, có thêm shortcut để tạo đoạn chat mới, tạo cửa sổ chat mới,… khá là tiện với những ai hay dùng shortcut như mình.

<br />

## Code - VSCode, PyCharm, Cursor, Trae

Quá nhiều thứ, nhưng mỗi cái dùng cho một vai trò khác nhau.
- **VSCode**: general purpose, dùng cho mọi loại dự án từ FE, BE, DevOps, Code C++… nói chung là cái gì cũng mở được, cũng đọc được, cũng dùng được tuốt. Mình dùng kèm với Github Copilot cho các tính năng AI.
- **Pycharm**: tập trung riêng cho python, cả backend lẫn làm AI. nhiều tính năng như quản lý kết nối database, ssh, quản lý môi trường ảo, indexing code, quản lý runtime, phiên bản python,… **tiện hơn**. Những cái này VSCode cũng làm được, nhưng qua nhiều extension trung gian, mình thì không thích điều ấy, mình muốn quản lý tất cả tập trung, đồng bộ, không hổ lốn, hỗn tạp, nên dùng Pycharm khi code Python, dù nó hơi nặng một chút khi so với C++ (à mình cũng dùng bản Student, có trong gói Student Pack của JetBrains x Github Student).
- **Cursor**: AI IDE, fork ra từ VSCode nên cái gì VSCode có thì Cursor cũng có, chỉ là tối giản hơn, giao diện hơi lạ, nhưng tập trung cho AI thì mình thấy ổn, thấy code hơn hẳn GPT, chế độ Agent cũng khá ổn, dù sẽ hết nhiều token (again, mình lại dùng gói Student Pack của cursor, free 1 năm nên sướng, chứ không thì cũng đau ví lắm hehe)
- **Trae**: khi chưa có Cursor free thì mình dùng cái này, cảm giác khá mạnh, hàng của ByteDance, ưu điểm lớn nhất là giống cursor và Free, model thì tất nhiên không mạnh bằng và nhiều lúc cao điểm thì phải In-queue khá lâu. Một ưu điểm khác thì là giao diện đẹp, rất clean. Mình vẫn biết ơn Trae vì khóa luận của mình chủ yếu code bằng thằng này, dù vẫn phải tối ưu (rất) nhiều =))

<br />

## Miscellaneous

- **Stickies**: tạo sticky note trên màn hình, có thể Always-on-top
- **Notes**: Note mấy cái linh tinh, tiện, đồng bộ với ipad, iphone
- **Reminders**: Nhắc lịch hẹn (cũng ít dùng)
- **Passwords**: Lưu mật khẩu, dành riêng cho các app hệ sinh thái apple. Mạnh, tiện, ổn định,  đồng bộ, free, tôi ưng.
- **Iphone Mirroring**: project cái màn hình iphone lên trên mac, tiện, siêu mượt, thi thoảng tiện khi không rảnh tay cầm thêm cái iphone hoặc khi đang cắm sạc iphone.
- **Gotiengviet**: Mình xem từ anh Duy Luân Dễ Thương bảo là dùng ổn nên mình dùng. Theo đánh giá là khá ổn, ổn hơn bộ gõ mặc định, thi thoảng vẫn xung đột nhẹ với Edge
- **Microsoft Word**, **Excel**, **Powerpoint**: Tải về cho có chứ cũng không phải dùng nhiều, cũng không thấy lỗi gì.
- **VMWare Fusion**: tạo và quản lý máy ảo Windows, Linux.
- …

to be updated.

<br/>






