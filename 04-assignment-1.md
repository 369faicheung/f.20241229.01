

<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>主題清單</title>
    <!-- Ionic CDN -->
    <script type="module" src="https://cdn.jsdelivr.net/npm/@ionic/core/dist/ionic/ionic.esm.js"></script>
    <script nomodule src="https://cdn.jsdelivr.net/npm/@ionic/core/dist/ionic/ionic.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@ionic/core/css/ionic.bundle.css" />
    <style>
      .item-content {
        width: 100%;
      }
      .item-title {
        font-weight: bold;
        margin: 0.25rem 0;
      }
      .item-subtitle {
        color: var(--ion-color-medium);
        font-size: 0.9em;
      }
      .tag-container {
        display: flex;
        flex-wrap: wrap;
        gap: 0.5rem;
        margin-top: 0.5rem;
      }
      .video-item {
        margin-top: 8px;
        width: 100%;
        max-height: 200px;
      }
    </style>
  </head>
  <body>
    <ion-app>
      <ion-header>
        <ion-toolbar>
          <ion-title>主題清單</ion-title>
        </ion-toolbar>
        <ion-searchbar placeholder="搜尋..."></ion-searchbar>
        <ion-item>
          <ion-select label="分類" interface="popover">
            <ion-select-option value="">全部</ion-select-option>
            <ion-select-option value="程式入門">程式入門</ion-select-option>
            <ion-select-option value="進階程式">進階程式</ion-select-option>
            <ion-select-option value="網頁設計">網頁設計</ion-select-option>
          </ion-select>
        </ion-item>
      </ion-header>

      <ion-content>
        <ion-list>
          <!-- 清單項目範本 -->
          <ion-item class="list-item">
            <div class="item-content">
              <div class="item-title">標題</div>
              <div class="item-subtitle">副標題</div>
              <div class="item-details">詳細資訊</div>
              <div class="tag-container">
                <ion-chip size="small">分類</ion-chip>
                <!-- 標籤 -->
              </div>
              <img class="video-item" src="images/example.jpg" alt="圖片" />
              <video class="video-item" controls>
                <source src="videos/example.mp4" type="video/mp4">
                您的瀏覽器不支援影片播放。
              </video>
            </div>
          </ion-item>
        </ion-list>
      </ion-content>
    </ion-app>

    <script>
      // 初始化資料
      let items = [
        {
          title: 'Python 基礎入門',
          language: 'Python 3',
          level: '入門',
          details: '從零開始學習 Python 程式設計，包含變數、流程控制、函式等基礎概念。',
          category: '程式入門',
          tags: ['Python', '程式設計', '入門課程'],
          imageUrl: 'images/python-basics.jpg',
          videoUrl: 'videos/python-intro.mp4',
        },
        // ... 增加其他項目，直到至少 20 個
      ];

      const searchbar = document.querySelector('ion-searchbar');
      const categorySelect = document.querySelector('ion-select');
      
      searchbar.addEventListener('ionInput', event => {
        updateList();
      });
      
      categorySelect.addEventListener('ionChange', event => {
        updateList();
      });

      function updateList() {
        const list = document.querySelector('ion-list');
        list.innerHTML = ''; // 清空清單

        const searchTerm = searchbar.value.toLowerCase();
        const selectedCategory = categorySelect.value;

        items.forEach(item => {
          const shouldDisplay =
            (item.title.toLowerCase().includes(searchTerm) || 
             item.details.toLowerCase().includes(searchTerm)) &&
            (selectedCategory === '' || item.category === selected

            