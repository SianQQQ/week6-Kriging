# Week 6 Student Worksheet: Spatial Prediction Shootout

Kriging vs Random Forest：將離散雨量站觀測轉為連續降雨面，比較四種空間內插方法（NN、IDW、Ordinary Kriging、RF），並分析 Kriging 獨有的不確定性估計（Sigma Map）。

## 分析流程

1. **資料載入**：CWA 鳳凰颱風雨量 JSON → 花蓮+宜蘭篩選 → EPSG:3826
2. **Variogram 分析**：Raw vs Log-transform、Spherical vs Exponential 模型比較
3. **四種內插**：NN、IDW、Ordinary Kriging、Random Forest（1000m 網格）
4. **不確定性分析**：Kriging Sigma Map + Nugget 效應比較
5. **GeoTIFF 輸出**：kriging_rainfall.tif、kriging_variance.tif、rf_rainfall.tif
6. **Zonal Statistics**：鄉鎮級降雨統計 + 可信度分級

## 資料來源

| 資料 | 來源 | 格式 |
|------|------|------|
| 雨量觀測 | CWA O-A0002-001（鳳凰颱風 2025/11/11） | JSON |
| 鄉鎮界 | 國土測繪中心 TGOS | Shapefile |

## 輸出檔案

- `Week6-Student.ipynb` — 完整分析 Notebook
- `interpolation_shootout.png` — 四種方法 2x2 比較圖
- `kriging_vs_rf.png` — Kriging vs RF 差異圖
- `sigma_map.png` — 降雨估計 + 不確定性地圖
- `*.tif` — GeoTIFF 輸出（EPSG:3826）

## 環境

```bash
source gis-env/bin/activate
pip install pykrige scipy scikit-learn matplotlib rasterio rasterstats
```
