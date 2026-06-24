# 🛣️ Road Segmentation System (道路影像分割系統)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green)
![NumPy](https://img.shields.io/badge/NumPy-latest-yellow)

本專案實作了一個基於傳統電腦視覺的道路分割任務。透過影像前處理、邊界偵測與透視幾何判斷等方法，將輸入的道路影像進行像素級（Pixel-level）分類，成功將畫面分割為「道路」與「非道路」兩大類別。

## 🎯 實驗目標

本專案的核心實驗目標如下：
- **實際道路分割功能**：建立穩定且具備幾何邏輯的視覺處理管線 (Pipeline)。
- **輸入**：一張道路場景圖片（RGB 格式）。
- **輸出**：
  1. 對應的分割遮罩（二值影像 Binary Mask）。
  2. 視覺化注水放大圖（Green Overlay Visualization）。
- **像素級分類**：
  - **類別 1**：道路（綠色注水區域）
  - **類別 0**：非道路（非綠色區域）

---

## ⚙️ 系統架構與演算法流程

本專案不依賴深度學習模型，而是採用純粹的電腦視覺幾何與特徵提取方法，確保系統的高效性與可解釋性。處理流程如下：

1. **影像前處理 (Preprocessing)**
   - 灰階化 (Grayscale Conversion)
   - 高斯模糊 (Gaussian Blur) 消除雜訊
2. **邊界偵測 (Edge Detection)**
   - 使用 Canny 邊緣偵測演算法提取影像中的高頻邊界特徵。
3. **透視幾何判斷與 ROI 擷取 (Perspective Geometry & ROI)**
   - 基於道路透視原理（消失點），建立感興趣區域（Region of Interest, ROI）遮罩，過濾掉天空與周遭無關背景。
4. **霍夫變換與道路範圍重建 (Hough Transform & Road Area Definition)**
   - 提取車道線特徵，並透過幾何計算擬合出道路的多邊形範圍。
5. **視覺化注水與像素級分類 (Visualization & Binary Mask)**
   - 產生類別 1（道路）的二值化遮罩。
   - 將綠色遮罩與原圖進行 Alpha Blending 融合，輸出最終結果。

---


## 📸 實驗成果與視覺化 (Experimental Results)

以下為本系統對實際道路場景的分割結果。我們將原始輸入、二值化遮罩與最終注水結果並排對比：



![成果圖](https://github.com/user-attachments/assets/7ea6c9ac-7e48-4864-afca-86fd14bccdf1)
pip install opencv-python numpy matplotlib
