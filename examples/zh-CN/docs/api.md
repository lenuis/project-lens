# API 约定

> 本文件集中记录接口输入、输出和错误语义，避免前后端与 AI 工具各自猜测字段。

## 创建预约

`POST /api/bookings`

```json
{
  "date": "2026-08-20",
  "slot": "14:30",
  "phone": "13800000000",
  "note": "靠窗位置"
}
```

## 预约状态

- `pending`：等待店主确认。
- `confirmed`：已确认。
- `completed`：已到店完成。
- `cancelled`：已取消但保留记录。
