# Wav

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```


html檔放置於文件根目錄
vue根組件放置於src資料夾以及vue組件放置於components資料夾

main.js : 註冊每頁html中根組件於此，以及導入fontawesome Icon 、 store.js狀態管理

index.html(對應App.vue)為首頁 : Corrusel1.vue -> 輪播圖，滑鼠移入時顯示左右箭頭，點擊左右箭頭或下方點換頁，而滑鼠移出後延遲收回箭頭
                               Item1.vue -> 限時搶購及每週新品部分透過Item1.vue及v-for組合顯示

Nav.vue為每頁上方導航 : 點擊 Wav圖示到index.html，
                      滑鼠移到男裝顯示導航欄 : 外套 -> jacket.html(app2.vue)
                                             長袖上衣 -> longSleeve.html(app5.vue)
                                             短袖上衣 -> shortSleeve.html(app6.vue)
                                             短褲 -> shorts.html(app7.vue)
                                             長褲 -> pants.html(app8.vue)
                                             春夏精選 -> summer.html(app9.vue)
                                             秋冬精選 -> winter.html(app10.vue)
                      滑鼠移到女裝顯示導航欄 : 外套 -> girlJacket.html(app11.vue)
                                             長袖上衣 -> girlLongClothes.html(app12.vue)
                                             短袖上衣 -> girlShortClohtes.html(app13.vue)
                                             短褲 -> girlShorts.html(app14.vue)
                                             長褲 -> girlPants.html(app15.vue)
                                             裙裝 -> girlDress.html(app16.vue)
                                             春夏精選 -> girlSummer.html(app17.vue)
                                             秋冬精選 -> girlWinter.html(app18.vue)

Component1.vue為每頁底部頁尾

Item1.vue : 將商品內容透過props傳遞給父組件，點擊立即購買按鈕觸發emit方法傳遞給父組件，再將數據傳遞給購物車。最後利用Transition組件包裝Item1，透過setTimeout切換條件呈現動畫

jacket.html(App2.vue)
longSleeve.html(App5.vue)
shortSleeve.html(App6.vue)
shorts.html(App7.vue)
pants.html(App8.vue)
summer.html(App9.vue)
winter.html(App10.vue)
girlJacket.html(App11.vue)
girlLongClothes.html(App12.vue)
girlShortClohtes.html(App13.vue)
girlShorts.html(App14.vue)
girlPants.html(App15.vue)
girlDress.html(App16.vue)
girlSummer.html(App17.vue)
girlWinter.html(App18.vue) : 各類商品架構相同，內容商品不同。 價格排序 : 透過sort方法將數據中的價格經由不同方式排序  由於種類眾多及數據龐大，加上需要將數據傳遞給購物車，因此利用狀態管理，創建store.js檔統一管理數據，這樣數據改變就能在不同網頁偵測。 因重新整理或進入其他頁面會導致數據重置而無法儲存至購物車，所以在每一次重新整理頁面前將數據儲存至localStorage解決問題。 點擊立即購買按鈕切換至shoppingcar.html(App3.vue)

store.js : 引入vuex使用狀態管理讓數據能夠給不同頁面使用。 儲存各類商品數據，提供遞增購物車及訂單方法給組件使用

shoppingcar.html(App3.vue) : 顯示各類商品購物車數量，透過v-show條件式顯示不同類區塊，假如count數量在1以上顯示，使用Item2.vue組件包裝。 點擊刪除按鈕將count設為0移除

Item2.vue : 將商品內容透過props傳遞給父組件，點擊結帳和刪除按鈕觸發emit方法傳遞給父組件，利用Transition組件包裝，setTimeout延遲顯示，position:relative將物件從左移入及opacity變為1。點擊前往結帳切換至order.html(App4.vue)

order.html(App4.vue) : 顯示各類商品訂單數量，透過v-show條件式顯示不同類區塊，假如order數量在1以上顯示，使用Item3.vue組件包裝。點擊刪除按鈕將order設為0

Item3.vue : 將商品內容透過props傳遞給父組件，點擊取消訂單按鈕觸發emit方法傳遞給父組件，利用Transition組件包裝Item1，setTimeout延遲顯示，position:relative將物件從左移入及opacity變為1。

brand.html(App19.vue)、privacy.html(App20.vue)、service.html(App21.vue) : 品牌故事 、 隱私權條款 、 聯絡客服文檔

響應式設計 : 在視窗寬度(1200px)時切換斷點， Nav.vue : 男裝、女裝變為flex column排列，導航欄改為直向排列
                                         Corrusel1.vue : 輪播圖寬度變為100%
                                         Item1.vue : margin增加
                                         Component1.vue : 變為 flex column排列
                                         Brand.html : 縮小字體
                                         shoppingcar.html(App3.vue)、order.html(App4.vue) : 寬度改為100%，縮小字體、margin







