---
name: amap-search
description: 高德地图周边搜索。用于查找指定地点附近的商家、服务设施。当用户询问"某地A附近有没有某地B"时使用，如：查找"科学城附近的汽车4S店"、"公司楼下的停车场"等。支持IP自动定位、关键字搜索、周边搜索、POI详情查询、地理编码。
version: 1.0.0
icon: 🗺️
---

# 高德地图周边搜索 (amap-search)

调用高德地图 Web 服务 API 搜索附近地点。

## 触发场景

当用户询问「附近/旁边有没有XX」时使用，例如：
- "帮我查一下附近哪里有洗车店"
- "我家楼下有停车场吗？"
- "公司旁边有药店吗？"

## 前置条件

1. 申请高德 API Key：https://lbs.amap.com/
2. 创建应用 → 添加 Key（选择 Web服务）
3. 免费配额：每天 2000 次

## 功能列表

| 命令 | 用途 |
|------|------|
| `ip` | 自动获取用户当前位置（IP定位） |
| `geo` | 地址转坐标 |
| `poi` | 关键字搜索 / 周边搜索 |

## 使用方式

### 1. 自动获取当前位置（IP定位）

```bash
python3 scripts/poi_search.py ip --key 你的API_KEY
```

### 2. 周边搜索

```bash
# 先获取位置，再用周边搜索
python3 scripts/poi_search.py ip --key 你的KEY
python3 scripts/poi_search.py poi --key 你的KEY --location "经度,纬度" --radius 5000 --keyword "洗车店"
```

### 3. 指定城市搜索

```bash
python3 scripts/poi_search.py poi --key 你的KEY --city 成都 --keyword "洗车店"
```

## 输出格式

- **JSON 输出**：支持 `--json` 参数
- **距离计算**：自动计算用户位置到 POI 的距离

## 注意事项

- IP定位是**粗略定位**，精确度取决于用户网络（通常到城市级别）
- 周边搜索半径默认 5000 米，最大 50000 米
