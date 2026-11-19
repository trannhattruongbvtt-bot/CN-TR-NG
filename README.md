<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="default" />
  <meta name="theme-color" content="#0f766e" />
  <title>KTV TRƯỜNG</title>
  <style>
    :root {
      --primary: #0f766e;
      --primary-dark: #115e59;
      --bg: #f1f5f9;
      --card: #ffffff;
      --text: #0f172a;
      --muted: #64748b;
      --danger: #dc2626;
      --warn: #d97706;
      --ok: #16a34a;
      --border: #e2e8f0;
    }

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    }

    body {
      margin: 0;
      background: var(--bg);
      color: var(--text);
      padding-bottom: 94px;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 20;
      background: var(--primary);
      color: #fff;
      padding: 14px 16px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.14);
    }

    header h1 {
      margin: 0;
      font-size: 18px;
      letter-spacing: 0.4px;
    }

    header span {
      font-size: 12px;
      opacity: 0.92;
    }

    .container {
      padding: 12px;
      max-width: 540px;
      margin: 0 auto;
    }

    .tab-content {
      display: none;
    }

    .tab-content.active {
      display: block;
    }

    .card {
      background: var(--card);
      border-radius: 14px;
      padding: 14px;
      margin-bottom: 12px;
      border: 1px solid var(--border);
      box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
    }

    .card-title {
      font-weight: 700;
      font-size: 15px;
      margin: 0 0 10px 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .grid-2 {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
    }

    label {
      display: block;
      font-size: 12px;
      font-weight: 600;
      color: var(--muted);
      margin: 8px 0 4px;
    }

    input, select, textarea {
      width: 100%;
      padding: 11px 12px;
      border: 1px solid var(--border);
      border-radius: 10px;
      font-size: 15px;
      background: #fff;
      color: var(--text);
    }

    input:focus, select:focus, textarea:focus {
      outline: none;
      border-color: var(--primary);
    }

    textarea {
      resize: vertical;
      min-height: 70px;
    }

    .btn {
      width: 100%;
      padding: 13px;
      border: none;
      border-radius: 12px;
      font-size: 15px;
      font-weight: 700;
      cursor: pointer;
      margin-top: 12px;
    }

    .btn:active { opacity: 0.85; }
    .btn-primary { background: var(--primary); color: #fff; }
    .btn-outline { background: #fff; color: var(--primary); border: 1.5px solid var(--primary); }
    .btn-danger { background: #fee2e2; color: var(--danger); }

    .btn-sm {
      padding: 6px 10px;
      font-size: 12px;
      border-radius: 8px;
      border: none;
      font-weight: 600;
      cursor: pointer;
    }

    .badge {
      padding: 3px 9px;
      border-radius: 999px;
      font-size: 11px;
      font-weight: 700;
      display: inline-block;
    }

    .badge-ok { background: #dcfce7; color: var(--ok); }
    .badge-warn { background: #fef3c7; color: var(--warn); }
    .badge-danger { background: #fee2e2; color: var(--danger); }

    .item-box {
      padding: 10px 0;
      border-bottom: 1px solid var(--border);
    }

    .item-box:last-child {
      border-bottom: none;
      padding-bottom: 0;
    }

    .item-header {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      gap: 8px;
      margin-bottom: 4px;
    }

    .chem-actions {
      display: flex;
      align-items: center;
      gap: 6px;
      margin-top: 8px;
    }

    .chem-btn {
      width: 36px;
      height: 36px;
      border-radius: 9px;
      border: 1px solid var(--border);
      background: #f8fafc;
      font-size: 18px;
      font-weight: 700;
      color: var(--primary);
      cursor: pointer;
    }

    .bottom-nav {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      height: 74px;
      background: #fff;
      border-top: 1px solid var(--border);
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      z-index: 30;
      padding-bottom: env(safe-area-inset-bottom);
    }

    .nav-item {
      border: none;
      background: none;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 4px;
      color: var(--muted);
      font-size: 12px;
      font-weight: 600;
      cursor: pointer;
    }

    .nav-item.active {
      color: var(--primary);
    }

    .nav-icon {
      font-size: 20px;
      line-height: 1;
    }

    .toast {
      position: fixed;
      top: 66px;
      left: 50%;
      transform: translateX(-50%);
      background: #0f172a;
      color: #fff;
      padding: 10px 18px;
      border-radius: 999px;
      font-size: 13px;
      font-weight: 600;
      z-index: 50;
      display: none;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    }
  </style>
</head>
<body>

  <header>
    <div>
      <h1>KTV TRƯỜNG</h1>
      <span id="todayDate">Sổ tay kỹ thuật viên xét nghiệm</span>
    </div>
    <span id="storageBadge" class="badge" style="background:rgba(255,255,255,0.2);color:#fff;">Đã kết nối bộ nhớ</span>
  </header>

  <div id="toast" class="toast">Đã lưu dữ liệu!</div>

  <div class="container">
    <!-- TAB 1: NHẬT KÝ QC & VẬN HÀNH -->
    <section id="tab-qc" class="tab-content active">
      <div class="card">
        <div class="card-title">Ghi nhận Nội kiểm (QC) / Kỹ thuật</div>
        
        <div class="grid-2">
          <div>
            <label>Thiết bị / Hệ thống</label>
            <select id="qcDevice">
              <option value="ABX 60 ES - Huyết học">ABX 60 ES - Huyết học</option>
              <option value="Máy Sinh hóa">Máy Sinh hóa</option>
              <option value="Máy Miễn dịch">Máy Miễn dịch</option>
              <option value="Máy Đông máu / Nước tiểu">Đông máu / Nước tiểu</option>
              <option value="Bảo trì / Hiệu chuẩn">Bảo trì / Hiệu chuẩn</option>
            </select>
          </div>
          <div>
            <label>Đánh giá kết quả</label>
            <select id="qcStatus">
              <option value="Đạt (Pass)">Đạt (Pass)</option>
              <option value="Theo dõi (Warn)">Theo dõi (Warn)</option>
              <option value="Lỗi / Chỉnh máy">Lỗi / Chỉnh máy</option>
            </select>
          </div>
        </div>

        <div class="grid-2">
          <div>
            <label>Số lô (Lot) QC / Hóa chất</label>
            <input type="text" id="qcLot" placeholder="VD: Lot 2409A" />
          </div>
          <div>
            <label>Người thực hiện / Ca trực</label>
            <input type="text" id="qcShift" value="KTV Trường" />
          </div>
        </div>

        <label>Chi tiết thông số & Xử lý kỹ thuật</label>
        <textarea id="qcNote" placeholder="VD: Chạy QC 3 mức đạt. Chỉnh Gain WBC theo lô hóa chất mới..."></textarea>

        <button type="button" class="btn btn-primary" id="btnSaveQc">+ Lưu bản ghi vào sổ</button>
      </div>

      <div class="card">
        <div class="card-title">
          <span>Lịch sử đã lưu</span>
          <span id="qcCount" style="font-size:12px;color:var(--muted);">0 mục</span>
        </div>
        <div id="qcList"></div>
      </div>
    </section>

    <!-- TAB 2: QUẢN LÝ HÓA CHẤT -->
    <section id="tab-chem" class="tab-content">
      <div class="card">
        <div class="card-title">
          <span>Tồn kho Hóa chất & Vật tư</span>
          <span id="chemCount" style="font-size:12px;color:var(--muted);">0 loại</span>
        </div>
        <div id="chemList"></div>
      </div>

      <div class="card">
        <div class="card-title">Nhập thêm hóa chất mới</div>
        <label>Tên hóa chất / dung dịch</label>
        <input type="text" id="newChemName" placeholder="VD: Diluent 20L, Cleaner 5L, Lyse 1L..." />
        
        <div class="grid-2">
          <div>
            <label>Số lượng nhập</label>
            <input type="number" id="newChemQty" value="1" min="0" step="0.5" />
          </div>
          <div>
            <label>Đơn vị tính</label>
            <input type="text" id="newChemUnit" placeholder="Bình, Can, Chai, ml..." />
          </div>
        </div>

        <div class="grid-2">
          <div>
            <label>Số lô (Lot)</label>
            <input type="text" id="newChemLot" placeholder="VD: L2611" />
          </div>
          <div>
            <label>Hạn sử dụng (HSD)</label>
            <input type="date" id="newChemExp" />
          </div>
        </div>

        <button type="button" class="btn btn-primary" id="btnAddChem">+ Thêm vào kho</button>
      </div>
    </section>

    <!-- TAB 3: NHẮC VIỆC & BẢO TRÌ -->
    <section id="tab-todo" class="tab-content">
      <div class="card">
        <div class="card-title">Thêm việc cần làm / Lịch bảo trì</div>
        <label>Nội dung công việc</label>
        <input type="text" id="todoInput" placeholder="VD: Rửa kim hút cuối ngày, dự trù hóa chất..." />
        <div class="grid-2">
          <div>
            <label>Mức độ ưu tiên</label>
            <select id="todoPriority">
              <option value="Hằng ngày">Hằng ngày</option>
              <option value="Gấp / Quan trọng">Gấp / Quan trọng</option>
              <option value="Định kỳ tuần/tháng">Định kỳ tuần/tháng</option>
            </select>
          </div>
          <div>
            <label>Hạn hoàn thành</label>

