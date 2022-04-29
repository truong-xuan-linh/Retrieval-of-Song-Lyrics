# **Retrieval of Song Lyrics**
## **Giới thiệu**
<img src= "https://github.com/truong-xuan-linh/Retrieval-of-Song-Lyrics/blob/master/AI-Challenge.png" width = "750" />

Retrieval of Song Lyrics là một cuộc thi về NLP được tổ chức bởi câu lạc bộ AI trường Đại học Công nghệ Thông tin. Nhiệm vụ là truy vấn tên bài hát từ danh sách các lyrics được cung cấp bởi Ban tổ chức
Mọi người có thể xem thêm chi tiết cuộc thi tại đây : https://www.kaggle.com/competitions/temporun-retrieval-of-song-lyrics
# **Các hướng đi đã thử**
Để giải quyết bài toán này, mình đã thử sức với nhiều phương pháp khác nhau.
## **Xử lý đầu vào**
Ở bước xử lý đầu vào. Vì không có nhiều thời gian dành cho cuộc thi nên mình chỉ thử nghiệm và test thử hai phương pháp chính, đó là:

**1. Sửa lỗi tiếng Việt ở những câu truy vấn**

Để có thể sửa lỗi tiếng Việt, mình đã tham khảo bài viết https://phamdinhkhanh.github.io/2020/05/28/TransformerThemDauTV.html của anh Phạm Đình Khánh và sau đó, tự tạo data bằng cách cắt nhỏ những lyrics mà ban tổ chức cung cấp, đưa hết về dạng không dấu để làm tập train. Kết quả nhận được khá tốt. Ví dụ về sửa dấu tiếng Việt có thể minh họa như sau:
```
input: Hom nay troi dep the nhi
output: Hôm nay trời đẹp thế nhỉ
```
**2. Chuyển đổi không dấu**

Phương pháp này hoàn toàn ngược lại với phương pháp ở trên, mình chuyển đổi toàn bộ câu truy vấn cũng như lyrics về dạng không dấu trước khi đưa vào mô hình nhằm mục đích tránh những lỗi không đáng có trong tiếng Việt. Ví dụ như:
```
input: truong, trường, trùong, trương
output: truong
```
## **Model xử lý**
Ở bước này, mình cũng thử nghiệm với hai mô hình chính, một là BM25, hai là mô hình cơ bản mà mình tự đề viết và đề xuất.

**1. BM25**

Trong bài toán retrieval, BM25 dường như đã quá nổi tiếng khi được phát triển từ TF-IDF

**2. Mô hình tự đề xuất**

Bên cạnh BM25, mình tự đề xuất một mô hình dựa trên ý tưởng của N-grams. Chi tiết về việc cài đặt nằm trong file jupyter notebook

# **Kết quả**

Kết quả cuối cùng khi mình kết hợp tất cả các phương pháp lại với nhau thì sự kết hợp giữa **chuyển đổi không dấu** và **mô hình tự đề xuất** cho ra kết quả tốt nhất, và mình nằm trong Top3 của cuộc thi.

<img src= "https://github.com/truong-xuan-linh/Retrieval-of-Song-Lyrics/blob/master/AI-Challenge-Results.png" width = "750" />
                
