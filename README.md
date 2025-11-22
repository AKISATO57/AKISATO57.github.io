[README.md](https://github.com/user-attachments/files/23660606/README.md)
# **🌸 AKISATOの世界 (AKISATO's World)**

「與其內卷，不如躺平看番。」

這是一個高度互動、動漫風格的個人主頁（Portfolio / Landing Page）。專案採用 **Single File Component (SFC)** 架構，無需複雜的構建工具（Webpack/Vite），直接透過現代瀏覽器的 ES Modules 支持，在單個 HTML 文件中運行完整的 React \+ Tailwind \+ Framer Motion 應用。

## **✨ 特色功能 (Features)**

### **🖥️ 視覺與交互**

* **極致的雙模光標系統 (Dual-Mode Cursor)**：  
  * **PC 端**：帶有物理彈簧（Spring Physics）慣性的光標，伴隨粒子拖尾特效，點擊時有毛玻璃質感的 Q 彈反饋。  
  * **Mobile 端**：針對 120Hz 高刷屏重寫的「零延遲」邏輯。繞過彈簧動畫，直接 1:1 跟隨手指坐標，並具備 0.5 秒自動閒置隱藏功能，徹底解決移動端卡頓問題。  
* **視差滾動 (Parallax)**：隨頁面滾動而滑動入場的動漫角色立繪。  
* **毛玻璃特效 (Glassmorphism)**：全站採用現代化的磨砂玻璃質感 UI。  
* **防干擾設計**：全域圖片防拖曳、精細化的文字選取控制（首屏描述可選中，其他均不可），提供類 App 的原生體驗。

### **🛠️ 功能整合**

* **Bangumi 番組計劃**：透過 API 實時獲取並展示個人的「在看」與「看過」番劇列表（支持異步加載與骨架屏 Loading）。  
* **Spotify 播放器**：內嵌歌單，帶有自定義的進入動畫。  
* **MikuTap 小遊戲**：集成了休閒解壓的 MikuTap 音樂遊戲模態框。  
* **社交媒體矩陣**：整合 Steam, Bilibili, GitHub, Twitter 等社交鏈接卡片（包含自定義繪製的 SVG 圖標）。

## **🚀 技術棧 (Tech Stack)**

本專案展示了如何在不使用 Node.js 構建流程的情況下，利用現代 Web 技術構建高性能應用：

* **Core**: HTML5 (ES Modules via importmap)  
* **Library**: [React 18](https://react.dev/) & ReactDOM (via esm.sh)  
* **Styling**: [Tailwind CSS](https://tailwindcss.com/) (CDN runtime)  
* **Animation**: [Framer Motion](https://www.framer.com/motion/) (用於複雜的物理動畫和佈局切換)  
* **Icons**: [Lucide React](https://lucide.dev/) & Custom SVG Paths  
* **Data**: fetch API & Bangumi API

## **📦 快速開始 (Getting Started)**

訪問 https://akihm.netlify.app/ 您可直接查看

## **⚙️ 配置 (Configuration)**

您可以在 index.html 的 \<script type="module"\> 標籤頂部找到 CONFIG 對象，在此處替換為您自己的信息：

const CONFIG \= {  
    userId: '648470',        // 您的 Bangumi 用戶 ID  
    avatar: '...',           // 頭像 URL  
    bgImage: '...',          // 背景圖 URL  
    featuredImg: '...',      // "關於我"部分的展示圖 URL  
    charaLeft: '...',        // 左側裝飾立繪  
    charaRight: '...',       // 右側視差立繪  
    spotifyUrl: '...',       // Spotify Embed URL  
    spotifyProfile: '...',   // Spotify 個人主頁鏈接  
};

## **📱 移動端優化細節**

為了在 iPhone Pro 等高刷設備上實現絲滑體驗，我們實施了以下優化：

* **Logic Separation**: 偵測 touchstart 事件，為 PC 和 Mobile 啟用兩套獨立的光標邏輯。  
* **Zero-Latency Tracking**: 觸摸模式下禁用物理彈簧，坐標 1:1 跟隨手指，杜絕延遲感。  
* **Performance**: 觸摸模式下完全禁用粒子生成，釋放 JS 線程和繪製壓力。  
* **Hardware Acceleration**: 關鍵動畫元素添加了 will-change: transform。  
* **Custom Scrollbar**: 為移動端導航欄定制了 3px 極細滾動條，提升美觀度。
