---
layout: post
title: "Giải đề thi chọn Đội tuyển quốc gia Tin 23-24 tỉnh Bắc Giang"
subtitle: ""
date: 2023-09-10 20:00:00 -0400
background: '/img/bg-04.png'
---

Hi, xin chào mọi người, hôm nay là 10/9, cũng là ngày diễn ra kỳ thi chọn Đội tuyển quốc gia của tỉnh Bắc Giang. Kể ra thì cũng lâu phết rồi tôi chưa đụng lại mấy đề này, từ hồi T9/2020 khi tôi vừa lên lớp 12 có tham gia kỳ thi chọn tội tuyển quốc gia lần cuối cùng, 2 năm sau thì cũng không đọc đề. Đến năm nay vừa tròn 3 năm, tôi có về dạy tiền đội tuyển cho các bạn nhỏ vài buổi, quen thêm vài bạn và cũng tự dưng thấy có quan tâm lại với VOI nên nay các em thi xong cũng có xin lại đề và giải thử xem sao. Thấy các idol toàn giải đề VOI, IOI các thứ, hay NVH thì giải đề thi đại học vật lý các kiểu, toi gà nên giải đề chơi chơi này thôi, trình bày cách AC đầu tiên nghĩ ra, chưa chỉnh sửa gì cả, các pro lướt qua thì gạch đá nhẹ nhàng nhé :)))

## Đánh giá chung

Đề bài: [link](https://drive.google.com/drive/folders/1KHtU5y7Wt-M5ej6YwGi0w7WWwXhFxwWc?usp=sharing)

Đọc qua đề một chút thì cũng khá đễ đoán ra đây là đề do giáo sư khác ra, vì chúng tôi cũng học 3 năm ở các thầy cô trong trường rồi, văn phong, style ra đề, độ khó thì cũng sẽ nắm được phần nào, nhưng đề này thì cũng tương đối lạ, có vẻ khá chắc kèo là được ra bởi một bên khác để đảm bảo tính công bằng nhất cho các thí sinh (năm nay có cả các bạn trong và ngoài CBG).

Về độ khó so với kỳ thi này ở Bắc Giang, thì tôi sẽ đánh giá ở mức phù hợp. Đề cũng không quá đánh đố, chia nhiều subtask cho từng lớp thí sinh, các sub khó thì cũng không phải dạng quá khó, đánh giá, suy luận 1 chút là ra. Với thời gian 180p, nhất là áp lực trong phòng thi thì tôi nghĩ sẽ không đủ để code lần lượt từng sub nên có lẽ các bạn sẽ phải đánh đổi một phương án an toàn hay muốn AC cả. Và cũng phải nói thêm rằng đề này so với các tỉnh mạnh như Hà Nội, Hải Phòng, Nam Định, Bắc Ninh thì có lẽ là quá dễ, cái này cũng phải thừa nhận, nhưng với tỉnh tôi, nơi phong trào tin học và đội tuyển tin cũng chưa mạnh lắm thì nhìn chung các em còn khá yếu và đề như này cũng gọi là vừa sức rồi 😐 

## Bài 1: Sôcôla

### Tóm tắt đề:

Có n viên kẹo, viên i có giá trị Ci.

Laura và Fran mua kẹo theo phương án: Nếu `Ci ≤ k` thì Laura trả hết tiền, nếu `Ci > k` thì Laura trả `K` còn Fran trả `Ci - k`

Mỗi truy vấn với giá trị `m` và `k` cho trước, tìm cách mua `m` viên kẹo sao cho (tổng số tiền Laura trả) - (tổng số tiền Fran trả là nhỏ nhất).

### Sub1: n, q ≤ 10^3

Dp gì đó mà tôi chưa nghĩ 😛

### Sub2: K1 = K2 =..=Kq, tức là số tiền Laura bỏ ra là cố định.

Sub này thì đơn giản rồi, ta xử lý các món đồ bên ngoài ngay từ đầu, bằng cách tính hiệu số tiền bỏ ra nếu phải mua mỗi món của Laura và Fran, lưu lại và sort lại thôi, mỗi truy vấn chỉ cần lấy `Mi` cái tối ưu nhất thôi. Bạn nào không làm được sub này xứng đáng trượt :)))

### Sub3: AC. n, q ≤ 10^5, Ci, Ki ≤ 10^9.

Nhận xét: 
- Thứ tự các truy vấn không quan trọng, mình có thể sắp xếp tùy ý.
- Thứ tự kẹo không quan trọng, mình cũng có thể sắp xếp tùy ý.

⇒ Note: Không hiểu sao đọc đề bài xong trong đầu tôi nó nghĩ ngay ra hướng “tích lũy” nên tòi ra hai cái nhận xét này, có vẻ khi code cũng hơi cồng kềnh nma tôi nghĩ 1 lúc thì thấy nó cũng AC nên thôi không nghĩ thêm cách khác nữa.

Ta thấy, việc mua kẹo của Laura và Fran sẽ có 3 trường hợp:

- Case 1: `Ci ≥ 2*k`: húp vội vì Ci càng lớn thêm nữa thì thằng Fran sẽ càng phải trả nhiều mà chi phí của Laura đã cố định → càng có lợi cho kết quả
- Case 2: `k ≤ Ci < 2*k`: trường hợp này Laura vẫn đang phải trả nhiều hơn, Ci càng cao thì sẽ càng “đỡ” âm cho kết quả.
- Case 3: `Ci < k`: trường hợp này chỉ Laura phải trả, chi phí của thằng Fran luôn là `0` đồng, nên ta sẽ expect giá càng thấp càng tốt, để Laura đỡ phải trả nhiều.

Ngay từ đầu sort lại `n` viên kẹo, tăng dần theo giá trị và sort lại `q` truy vấn theo `k` tăng dần. Khi đó các viên kẹo sẽ chia thành 3 nhóm.

<div style="width: 100%;">
  <img src="https://raw.githubusercontent.com/nyvietnam/mjml/main/cdt-anh1.png" style="width: 100%;">
</div>

Vẽ đến đây chắc mọi người cũng hình dung được sương sương nên làm như thế nào rồi. Đầu tiên, ở nhánh `Ci > 2k`, ta lấy ngược lại từ cuối về, nếu đủ `Mi` rồi thì thôi, nếu vẫn chưa đủ `Mi` thì ta sẽ lấy tiếp ở hai nhóm kia. Ở hai nhóm còn lại, ta duy trì 2 con trỏ như 2 mũi tên hình vẽ, mỗi lần chọn xem lấy ở bên nào tối ưu hơn thôi.

Nói chung là khá dễ và khá dễ code, bạn nào tự tin thì đấm AC luôn chứ còn gì nữa.

## Bài 2: Phần thưởng

### Tóm tắt đề

Có `n` phần quà, quà `i` có giá trị `Ai` có thể âm. Có `K` học sinh, mỗi học sinh sẽ nhận một dãy **liên tiếp** các quà trong `n` phần quà đó.

- Mỗi học sinh có thể có quà hoặc không, có thì phải là dãy liên tiếp.
- Mỗi quà có thể trao hoặc không, nếu trao chỉ trao cho một người.

⇒ Chọn trong dãy độ dài `N` ban đầu: `x` dãy con liên tục không giao nhau (`x ≤ k`) sao cho tổng x dãy con lớn nhất.

### Sub 1: tối đa 1 quà có giá trị âm.

Nếu `K= 1` thì làm bằng tổng tiền tố.

Nếu `K > 1` thì đáp án là tổng tất cả phần quà bỏ đi phần quà âm.

### Sub 2: K = 1.

Tổng tiền tố.

### Sub 3: 1 ≤ K ≤ N ≤ 80

(chắc là) DP `n^4` nhưng tôi chưa nghĩ.

### Sub 4: 80 ≤ K ≤ N ≤ 300

(chắc là) DP `n^3` nhưng tôi chưa nghĩ.

### Sub 5: AC. 300 ≤ K ≤ N ≤ 2000.

DP cơ bản + tổng tiền tố.

`F[i, k]` xét đến `i` đã tạo ra được `K` dãy con và `i` là điểm cuối của dãy con thứ `K`.

Khi đó, `F[i, k] = max(F[j, k-1]) +` dãy con lớn nhất tạo được với i là điểm cuối. Chỗ này đơn giản có thể dùng deque để duy trì & tìm tổng tiền tố nhỏ nhất trong đoạn [j+1..i] thôi, khá đơn giản.

<div style="width: 100%;">
  <img src="https://raw.githubusercontent.com/nyvietnam/mjml/main/cdt-anh2.png" style="width: 100%;">
</div>

## Bài 3: Đếm kim cương

Định nghĩa Kim cương: như hình dưới và viền là ký tự `#`, bên trong **hoàn toàn** là ký tự `.`. Đếm số kim cương trong input đầu bài cho.

<div style="width: 100%;">
  <img src="https://raw.githubusercontent.com/nyvietnam/mjml/main/cdt-anh3.png" style="width: 100%;">
</div>

### Sub 1: 1 ≤ n,m ≤ 100, bảng chỉ chứa viên kim cương nhỏ nhất.

Không cần nghĩ cũng làm được. Duyệt cả bảng, với mỗi ô `#` giả định nó là đáy của viên kim cương, xét 4 ô bên trên xem sao.

### Sub 2: 1 ≤ n,m ≤ 100

(chắc là) chặn đầu chặn đuôi, xong duyệt tuần tự bên trong để kiểm tra → `n^4`

### Sub 3: AC. 100 ≤ n, m ≤ 2000

Bài này đọc 1 cái là thấy giống giống bài DIST2 đúng 3 năm trước cũng trong kỳ thi này, mình không AC hôm đấy nhưng về nhà đã làm được bằng phương pháp tự nghĩ ra: **tổng tích lũy chéo**. Cách này gần như không thấy ai dùng, kể cả các thầy hay giáo sư hay những người mà tôi học cùng, nma tôi thấy nó cũng khá đơn giản & dễ hiểu thôi.

<div style="width: 100%;">
  <img src="https://raw.githubusercontent.com/nyvietnam/mjml/main/cdt-anh4.png" style="width: 100%;">
</div>

Nhưng lần này tôi sẽ không dùng tổng tích lũy chéo để tính tổng, mà tôi sẽ dùng `F[i,j]` để lưu khoảng cách của mỗi ô `#` đến ô `#` gần nhất phía trái trên theo đường chéo.

Giờ thì tôi sẽ for 2 vòng để xét tất cả mọi điểm và giả dụ nó là điểm đáy của viên kim cương. Tiếp theo, xác định đỉnh của viên kim cương (nhận xét: với mỗi đáy nó chỉ nhận duy nhất một điểm theo trục dọc là đỉnh, chính là điểm gần nhất bên trên mà có dấu `#`). Nếu điểm tìm được có khoảng cách với đáy là chẵn thì lập tức loại luôn, vì chiều cao của kim cương luôn lẻ.

Có đáy có đỉnh là ta xác định được 2 điểm bên một cách dễ dàng. Bây giờ chỉ cần đảm bảo 2 cạnh bên dưới của kim cương cách đều hai đường chéo của nó là xong. Tức là với mỗi điểm `[i,j]` nằm trên đường nối giữa điểm đáy của kim cương với điểm bên phải thì `F[i, j]` luôn bằng nhau và bằng đúng độ dài đường đó là được. Phía còn lại làm tương tự là xong.

## Kết luận

Nói chung tôi thấy đề cũng khá dễ, nhưng cũng cần các bạn khi học chịu khó code nhiều, mỗi bài có 2/3 hoặc 3/5 task trâu rồi, thì tổng lại cả đề thì hoàn toàn có thể làm trâu 12/20 mà không cần suy nghĩ gì. Tuy nhiên, như đã nói bên trên thì chất lượng đội dự tuyển của trường tôi cũng không phải quá là mạnh, nhất là về phần coding sau mấy buổi dạy thì tôi cảm giác các em khá là yếu và linh cảm là làm bài này sẽ không chắc tay được. Thi xong có hỏi 1 đồng chí đợt tôi dạy làm bài khá tốt nhưng mà cũng kêu code bug =)))) Thôi thì chọn lọc tự nhiên thôi, bạn nào chăm chỉ code, code chắc tay thì sẽ làm được kha khá. Tuy nhiên thì tôi thấy đề này hơi thiên về DP, với các bạn học tiền đội tuyển của CBG thì phải học nhiều thứ hơn thế rất là nhiều như Cấu trúc dữ liệu, Duyệt hay Đồ thị,… mà thi vào DP thì các bạn nào giỏi các mảng kia mà yếu DP thì sẽ cảm thấy hơi bất công 1 chút. Anyway, dù thiên về DP nhưng cũng là DP dễ, các sub trâu, cơ bản mà không làm được thì cũng không trách ai được nữa rồi.



<br>
<br>
<br>

