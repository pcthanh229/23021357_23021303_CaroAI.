# Bài Tập Lớn Giữa Kì Caro AI

## Thành viên

- 23021357 - Phạm Công Thành

## Giới thiệu

Chương trình chơi cờ Caro AI áp dụng thuật toán **Minimax** và **Alpha-Beta Pruning**.

- Kích thước bàn cờ: **9x9**
- Luật chơi: **4 quân liên tiếp** theo hàng ngang, hàng dọc hoặc đường chéo là thắng.
- Không xét luật chặn hai đầu.
- Người chơi là **X**, máy tính là **O**.
- Giao diện: **Tkinter đồ họa đơn giản**, có cửa sổ riêng để chơi game.
- Chương trình có hỗ trợ đo đạc số trạng thái đã xét và thời gian chạy của thuật toán.

## Cài đặt môi trường

Cài đặt Python phiên bản 3.x.

Project sử dụng thư viện **tkinter**, thư viện này thường có sẵn khi cài Python trên Windows.

Nếu muốn kiểm tra hoặc cài đặt theo file yêu cầu, mở terminal tại thư mục gốc và chạy:

```bash
pip install -r requirements.txt
Cách chạy chương trình
1. Chạy game với AI

Mở terminal tại thư mục gốc của project, sau đó chạy:

cd source_code
python main.py

Sau khi chạy, cửa sổ game Caro sẽ xuất hiện. Người chơi bấm chuột vào ô trên bàn cờ để đánh quân X, sau đó máy tính sẽ tự động tính toán và đánh quân O.

Trong giao diện, người chơi có thể chọn:

Thuật toán AI: Minimax hoặc Alpha-Beta
Độ sâu tìm kiếm
Bắt đầu ván mới
2. Chạy theo từng mức yêu cầu
Level 1 - Minimax
cd level1_minimax
python main_level1.py

Level này cài đặt trò chơi Caro giữa người và máy, trong đó máy sử dụng thuật toán Minimax có giới hạn độ sâu.

Level 2 - Alpha-Beta Pruning
cd level2_alphabeta_gui
python main_level2_gui.py

Level này phát triển thêm thuật toán Alpha-Beta Pruning nhằm giảm số trạng thái cần xét so với Minimax.

Level 3 - Thực nghiệm và đánh giá
cd level3_experiment
python benchmark_level3.py

Script này chạy các trạng thái kiểm thử khác nhau để so sánh giữa Minimax và Alpha-Beta về:

Nước đi được chọn
Giá trị đánh giá
Số trạng thái đã xét
Thời gian chạy

Sau khi chạy, chương trình có thể tạo file kết quả:

benchmark_results.csv

File này dùng để đưa vào phần bảng kết quả thực nghiệm trong báo cáo.

Các module chính
board.py: Cài đặt bàn cờ 9x9, kiểm tra nước đi hợp lệ, đánh quân, hoàn tác nước đi, kiểm tra thắng/thua và hòa.
ai.py: Cài đặt thuật toán Minimax, Alpha-Beta Pruning, chọn nước đi tốt nhất, đếm số trạng thái đã xét và đo thời gian chạy.
evaluate.py: Cài đặt hàm heuristic đánh giá trạng thái bàn cờ dựa trên các chuỗi quân 2, 3, 4 quân của người chơi và máy.
main.py: File chạy chính của chương trình có giao diện đồ họa.
main_gui.py: Cài đặt giao diện Tkinter, vẽ bàn cờ, xử lý click chuột và hiển thị thông tin thuật toán.
main_console.py: Phiên bản chạy bằng console.
benchmark.py: Cài đặt các trạng thái kiểm thử để đo đạc và so sánh hiệu quả giữa Minimax và Alpha-Beta.
Cấu trúc thư mục
23021357_CaroAI/
├── source_code/
│   ├── board.py
│   ├── evaluate.py
│   ├── ai.py
│   ├── main.py
│   ├── main_gui.py
│   └── benchmark.py
│
├── level1_minimax/
│   ├── board.py
│   ├── evaluate.py
│   ├── ai.py
│   └── main_level1.py
│
├── level2_alphabeta_gui/
│   ├── board.py
│   ├── evaluate.py
│   ├── ai.py
│   └── main_level2_gui.py
│
├── level3_experiment/
│   ├── board.py
│   ├── evaluate.py
│   ├── ai.py
│   └── benchmark_level3.py
│
│
├── requirements.txt
└── README.md
Thuật toán sử dụng
Minimax

Minimax là thuật toán tìm kiếm trong trò chơi đối kháng hai người. Thuật toán giả định rằng cả người chơi và máy đều chọn nước đi tối ưu.

Máy tính là người chơi MAX, cố gắng chọn nước đi có điểm đánh giá lớn nhất.
Người chơi là MIN, được giả định sẽ chọn nước đi làm giảm lợi thế của máy.
Khi đạt độ sâu giới hạn hoặc trạng thái kết thúc, thuật toán dùng hàm đánh giá để tính điểm.
Alpha-Beta Pruning

Alpha-Beta Pruning là cải tiến của Minimax nhằm giảm số nhánh cần duyệt.

alpha: giá trị tốt nhất hiện tại của MAX.
beta: giá trị tốt nhất hiện tại của MIN.
Nếu beta <= alpha, thuật toán cắt nhánh vì nhánh đó không còn ảnh hưởng đến kết quả cuối cùng.

Alpha-Beta thường cho cùng kết quả với Minimax khi dùng cùng độ sâu và cùng hàm đánh giá, nhưng xét ít trạng thái hơn và chạy nhanh hơn.

Hàm đánh giá trạng thái

Hàm đánh giá dựa trên các thế cờ của máy và người chơi:

Máy có 4 quân liên tiếp: điểm rất lớn.
Người chơi có 4 quân liên tiếp: điểm rất nhỏ.
Máy có 3 quân liên tiếp: điểm cao.
Người chơi có 3 quân liên tiếp: điểm âm lớn để ưu tiên chặn.
Máy có 2 quân liên tiếp: điểm dương nhỏ.
Người chơi có 2 quân liên tiếp: điểm âm nhỏ.

Cách đánh giá này giúp AI vừa có khả năng tấn công, vừa ưu tiên phòng thủ khi người chơi có nguy cơ thắng.

Kết quả thực nghiệm

Chương trình có phần benchmark để kiểm thử trên nhiều trạng thái bàn cờ khác nhau, ví dụ:

Trạng thái đầu ván.
Trạng thái giữa ván.
Trạng thái máy có thể thắng ngay.
Trạng thái người chơi sắp thắng, máy cần chặn.
Trạng thái hai bên đều có cơ hội tấn công.

Kết quả thực nghiệm được dùng để so sánh:

Minimax và Alpha-Beta có chọn cùng nước đi hay không.
Alpha-Beta giảm được bao nhiêu trạng thái so với Minimax.
Thời gian chạy thay đổi như thế nào khi tăng độ sâu.
Độ sâu tìm kiếm ảnh hưởng thế nào đến chất lượng nước đi.
