# Báo cáo: Bài 1 - Khôi phục commit đã mất bằng Git Reflog

## Các bước khôi phục commit
1. **Khởi tạo và chuẩn bị (Giả lập lỗi):**
   - Đã tạo commit với nội dung `"Them tinh nang quan trong"`.
   - Vô tình chạy lệnh lùi lại 1 commit:
     ```bash
     git reset --hard HEAD~1
     ```
   - Lúc này, kiểm tra `git log --oneline` sẽ không còn thấy commit đó nữa và thư mục làm việc đã bị mất file.

2. **Tra cứu Reflog:**
   - Để tìm lại lịch sử tham chiếu (kể cả những commit đã bị xóa khỏi log hiện tại), ta sử dụng lệnh:
     ```bash
     git reflog
     ```
   - Kết quả xuất hiện:
     ```text
     03c7edc HEAD@{0}: reset: moving to HEAD~1
     a72d8d3 HEAD@{1}: commit: Them tinh nang quan trong
     03c7edc HEAD@{2}: commit (initial): Initial commit
     ```
   - Qua đây, ta xác định được mã hash của commit chứa tính năng quan trọng là `a72d8d3`.

3. **Khôi phục commit:**
   - Dùng lệnh `git reset --hard <mã-hash>` để khôi phục trạng thái nhánh làm việc về đúng commit đó:
     ```bash
     git reset --hard a72d8d3
     ```
   - Sau lệnh này, commit đã biến mất được khôi phục thành công, file và nội dung đều đã trở lại thư mục làm việc.

## Kết quả kiểm tra
(Học viên vui lòng chạy `git log --oneline` và `git reflog` trên máy tính rồi chèn ảnh chụp màn hình vào đây)
