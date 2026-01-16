# ESS - Embeddings Semantic Search 🔍

Một hệ thống tìm kiếm ngữ nghĩa (Semantic Search) sử dụng **AI và Machine Learning** để tìm kiếm tài liệu dựa trên ý nghĩa thay vì chỉ từ khóa.

## 📋 Mô tả dự án

Dự án này cung cấp các công cụ để:
- **Tìm kiếm ngữ nghĩa**: Tìm kiếm dựa trên ý nghĩa của câu hỏi, không chỉ từ khóa
- **Mã hóa văn bản**: Chuyển đổi văn bản thành vector số bằng AI
- **So sánh độ tương tự**: Sử dụng cosine similarity để tìm kết quả phù hợp nhất
- **API Server**: Cung cấp REST API cho các ứng dụng khác
- **Hệ thống chat thông minh**: Hỗ trợ giao tiếp tự nhiên với lịch sử câu hỏi

## 🎯 Tính năng chính

✅ **Hỗ trợ đa ngôn ngữ** - Bao gồm Tiếng Việt  
✅ **Tìm kiếm nhanh** - Sử dụng vector embedding  
✅ **API RESTful** - Dễ tích hợp vào ứng dụng  
✅ **Mô-đun hóa** - Code sạch, dễ bảo trì  
✅ **Chat tương tác** - Giao diện dòng lệnh thân thiện

## 📁 Cấu trúc dự án

```
semantic_search_project/
├── api.py           # FastAPI server cho tìm kiếm
├── demo.py          # Ví dụ cơ bản về embedding
├── search.py        # Module tìm kiếm ngữ nghĩa
├── system.py        # Hệ thống chat thông minh với bộ nhớ
├── requirements.txt # Các thư viện cần thiết
└── README.md        # File này
```

## 🚀 Cách sử dụng

### 1. Cài đặt dependencies

```bash
pip install -r requirements.txt
```

**Thư viện chính:**
- `fastapi` - Web framework
- `sentence-transformers` - AI model cho embedding
- `scikit-learn` - Cosine similarity
- `numpy` - Xử lý mảng số
- `uvicorn` - Server ASGI

### 2. Chạy ví dụ đơn giản

```bash
python demo.py
```

Output mong đợi:
```
--- Đang tải mô hình AI... ---
Thành công!
Máy đã biến 2 câu văn thành vector có kích thước: (2, 384)
Vector của câu đầu tiên trông như thế này (rút gọn): [-0.05... 0.12... ...]
```

### 3. Chạy tìm kiếm ngữ nghĩa

```bash
python search.py
```

Ví dụ:
```
Câu hỏi của bạn: Làm thế nào để lập trình?
--> Kết quả tìm thấy: "Cách cài đặt Python trên Windows rất dễ"
--> Độ chính xác: 0.6234 (Càng gần 1 càng chuẩn)
```

### 4. Chạy hệ thống chat thông minh

```bash
python system.py
```

Hệ thống sẽ:
- Lưu lịch sử câu hỏi
- Tự động phân loại câu hỏi (đơn giản vs phức tạp)
- Tìm kiếm các tài liệu phù hợp

```
Bạn (Gõ câu hỏi): Cách nấu phở?
[Memory] Đã nhớ 1 câu hỏi trong phiên này.
--> Kết quả tìm thấy: "Công thức nấu món phở bò Nam Định chuẩn vị"
--> Độ chính xác: 0.7891

Bạn (Gõ câu hỏi): exit
```

### 5. Chạy API Server

```bash
python -m uvicorn api:app --reload
```

Sau đó truy cập:
- **Swagger UI**: http://localhost:8000/docs
- **API Endpoint**: POST http://localhost:8000/search

**Ví dụ request:**
```bash
curl -X POST "http://localhost:8000/search" \
  -H "Content-Type: application/json" \
  -d '{"text": "Cách cài đặt Python"}'
```

**Response:**
```json
{
  "status": "success",
  "question": "Cách cài đặt Python",
  "best_match": "Hướng dẫn cài đặt Python",
  "score": 0.8654
}
```

## 🤖 Cách thức hoạt động

### Embedding (Mã hóa văn bản)
```
Câu hỏi: "Cách nấu phở?"
         ↓
  Sentence Transformer
         ↓
Vector: [0.12, -0.45, 0.67, ...]  (384 chiều)
```

### Tìm kiếm
```
Query Vector → Cosine Similarity → So sánh với tất cả docs
              ↓
          Tìm doc có score cao nhất
              ↓
          Trả về kết quả tốt nhất
```

## 📊 Model AI được sử dụng

- **`paraphrase-multilingual-MiniLM-L12-v2`**: Hỗ trợ 50+ ngôn ngữ, kích thước nhẹ
- **`all-MiniLM-L6-v2`**: Model Tiếng Anh tối ưu hóa

## 🔧 Công nghệ

- **Python 3.8+**
- **Sentence Transformers** (BERT-based)
- **Scikit-learn** (Cosine Similarity)
- **FastAPI** (REST API)
- **NumPy** (Xử lý số)

## 📈 Cải thiện trong tương lai

- [ ] Lưu trữ documents trong database
- [ ] Hỗ trợ upload file (PDF, TXT)
- [ ] Fine-tune model cho domain cụ thể
- [ ] Cache results để tối ưu hiệu suất
- [ ] Thêm authentication cho API
- [ ] Giao diện web (Frontend)

## 📝 License

MIT License - Tự do sử dụng cho các dự án cá nhân và thương mại.

## 👤 Tác giả

**Tienkute** - [GitHub Profile](https://github.com/Tienkute)

## 📞 Liên hệ & Hỗ trợ

- 📧 Email: [Liên hệ qua GitHub]
- 🐛 Issues: [GitHub Issues](https://github.com/Tienkute/ESS/issues)

---

**Happy Searching! 🚀**

Nếu bạn thấy dự án này hữu ích, vui lòng cho ⭐ trên GitHub!
