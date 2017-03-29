長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
ptt1<-"https://www.ptt.cc/bbs/movie/index.html"
pttcontent1<-read_html(ptt1)
post_title1<-pttcontent1%>%html_nodes(".title")%>%html_text()
post_title1
```

    ## [1] "\n\t\t\t\n\t\t\t\t[情報] 我和我的冠軍女兒臺北票房\n\t\t\t\n\t\t\t"             
    ## [2] "\n\t\t\t\n\t\t\t\t[新聞] 韓版不能說的秘密明年開拍 網友不買單\n\t\t\t\n\t\t\t"  
    ## [3] "\n\t\t\t\n\t\t\t\t[新聞] 莊凱勛拍目擊者 認真相也許沒那麼重要\n\t\t\t\n\t\t\t"  
    ## [4] "\n\t\t\t\n\t\t\t\t[普雷] 金剛戰士 Power Rangers-追的是一段青春\n\t\t\t\n\t\t\t"
    ## [5] "\n\t\t\t\n\t\t\t\t[問片] 找部年代久遠香港有紙紮人的鬼片\n\t\t\t\n\t\t\t"       
    ## [6] "\n\t\t\t\n\t\t\t\t[公告]《各式疑難雜症FAQ》\n\t\t\t\n\t\t\t"                   
    ## [7] "\n\t\t\t\n\t\t\t\t[公告] 板規！必看！｜好文推薦‧惡文檢舉\n\t\t\t\n\t\t\t"      
    ## [8] "\n\t\t\t\n\t\t\t\t[贈票] 湯姆漢克斯大力推薦《衝突的一天》贈票\n\t\t\t\n\t\t\t"

``` r
post_author1<-pttcontent1%>%html_nodes(".author")%>%html_text()
post_author1
```

    ## [1] "lovelandbird" "iam168888888" "iam168888888" "practice24"  
    ## [5] "xxshoxx"      "yunyun85106"  "ericf129"     "pelicula"

``` r
post_good1<-pttcontent1%>%html_nodes(".nrec")%>%html_text()
post_good1
```

    ## [1] "1"  "3"  "5"  "2"  ""   "23" "爆" "爆"

``` r
library(rvest)
html<-read_html("https://www.ptt.cc/bbs/movie/index.html")
btnurl<-html%>%html_nodes("a[class='btn wide']")%>%html_attr("href")
indexnum<-as.numeric(gsub("/bbs/movie/index|.html","",btnurl[2]))
for(i in(indexnum-3):(indexnum+1)){
  #print(i)
  print(paste0("https://www.ptt.cc/bbs/movie/index",i,",html"))
}
```

    ## [1] "https://www.ptt.cc/bbs/movie/index5280,html"
    ## [1] "https://www.ptt.cc/bbs/movie/index5281,html"
    ## [1] "https://www.ptt.cc/bbs/movie/index5282,html"
    ## [1] "https://www.ptt.cc/bbs/movie/index5283,html"
    ## [1] "https://www.ptt.cc/bbs/movie/index5284,html"

``` r
ptt2<-"https://www.ptt.cc/bbs/movie/index5279.html"
pttcontent2<-read_html(ptt2)
post_title2<-pttcontent2%>%html_nodes(".title")%>%html_text()
post_title2
```

    ##  [1] "\n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t"                                   
    ##  [2] "\n\t\t\t\n\t\t\t\t[ 普雷]好像沒人看過的《斧視眈眈 \n\t\t\t\n\t\t\t"                               
    ##  [3] "\n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t"                                   
    ##  [4] "\n\t\t\t\n\t\t\t\t[大好雷] 我和我的冠軍女兒-近期最愛電影\n\t\t\t\n\t\t\t"                         
    ##  [5] "\n\t\t\t\n\t\t\t\t[好雷] 看情懷的金剛戰士\n\t\t\t\n\t\t\t"                                        
    ##  [6] "\n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t"                                   
    ##  [7] "\n\t\t\t\n\t\t\t\t[討論] 我和我的冠軍女兒 大女兒（有雷）\n\t\t\t\n\t\t\t"                         
    ##  [8] "\n\t\t\t\n\t\t\t\t[選片] 本能寺大飯店vs金剛戰士\n\t\t\t\n\t\t\t"                                  
    ##  [9] "\n\t\t\t\n\t\t\t\t[普雷] 聲之形-如果今天被80的是醜女\n\t\t\t\n\t\t\t"                             
    ## [10] "\n\t\t\t\n\t\t\t\t[討論] 試映形式及其所代表意義\n\t\t\t\n\t\t\t"                                  
    ## [11] "\n\t\t\t\n\t\t\t\t[討論] 愛是您愛是我續集\n\t\t\t\n\t\t\t"                                        
    ## [12] "\n\t\t\t\n\t\t\t\t[新聞] 《八月》：人啊，你是否低下過高貴的頭顱\n\t\t\t\n\t\t\t"                  
    ## [13] "\n\t\t\t\n\t\t\t\t[討論] 這幾年還有什麼值得推薦的好萊塢動作片\n\t\t\t\n\t\t\t"                    
    ## [14] "\n\t\t\t\n\t\t\t\t[情報] 傑克葛倫霍主演波士頓馬拉松爆炸案電影《Stronger》由獅門影\n\t\t\t\n\t\t\t"
    ## [15] "\n\t\t\t\n\t\t\t\t[討論] 攻殼機動隊 該看3D?或4D?\n\t\t\t\n\t\t\t"                                 
    ## [16] "\n\t\t\t\n\t\t\t\t[新聞] 《猜火車2》道具慈善拍賣　卑比坐牢用的\n\t\t\t\n\t\t\t"                   
    ## [17] "\n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t"                                   
    ## [18] "\n\t\t\t\n\t\t\t\t[請益] 我和我的冠軍女兒 \n\t\t\t\n\t\t\t"                                       
    ## [19] "\n\t\t\t\n\t\t\t\t[討論] 銀魂真人版\n\t\t\t\n\t\t\t"                                              
    ## [20] "\n\t\t\t\n\t\t\t\t[討論] Captain Underpants 首回預告\n\t\t\t\n\t\t\t"

``` r
post_author2<-pttcontent2%>%html_nodes(".author")%>%html_text()
post_author2
```

    ##  [1] "SQUAD12345"   "lunanightcat" "t13thbc"      "loveponpon"  
    ##  [5] "amy3692"      "ckshchen"     "ilovepitaya"  "aff002377"   
    ##  [9] "newshooter"   "alljerry04"   "AceRocker"    "JackAC"      
    ## [13] "MgcnVanish"   "qpr322"       "nardus"       "ourstage"    
    ## [17] "linkcat"      "anher"        "KingKingCold" "debb0128"

``` r
post_good2<-pttcontent2%>%html_nodes(".nrec")%>%html_text()
post_good2
```

    ##  [1] "3"  ""   "10" "4"  "11" "35" "9"  "14" "8"  "3"  "28" "9"  "7"  "7" 
    ## [15] "15" "2"  "6"  "20" "53" "1"

``` r
ptt3<-"https://www.ptt.cc/bbs/movie/index5278.html"
pttcontent3<-read_html(ptt3)
post_title3<-pttcontent3%>%html_nodes(".title")%>%html_text()
post_title3
```

    ##  [1] "\n\t\t\t\n\t\t\t\tRe: [情報] 帝國戰神：巴霍巴利王 好萊塢電影台首播\n\t\t\t\n\t\t\t"           
    ##  [2] "\n\t\t\t\n\t\t\t\t[新聞] 獅門影業或將拍攝5-7集金剛戰士！\n\t\t\t\n\t\t\t"                     
    ##  [3] "\n\t\t\t\n\t\t\t\t[新聞] 《金剛戰士》導演爆料續集將有經典角色\n\t\t\t\n\t\t\t"                
    ##  [4] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [Kobe2630]\n\t\t\t\n\t\t\t"                                  
    ##  [5] "\n\t\t\t\n\t\t\t\t[新聞] 賀歲片王豬哥亮驚傳離世？經紀人指尚未證實\n\t\t\t\n\t\t\t"            
    ##  [6] "\n\t\t\t\n\t\t\t\t[閒聊] 搞不懂梁朝偉演技到底哪裡好\n\t\t\t\n\t\t\t"                          
    ##  [7] "\n\t\t\t\n\t\t\t\t[新聞] 美女與野獸奪北美台灣雙週冠軍有望出外傳\n\t\t\t\n\t\t\t"              
    ##  [8] "\n\t\t\t\n\t\t\t\t[好雷] 美女與野獸 卡通與真人不一樣的地方\n\t\t\t\n\t\t\t"                   
    ##  [9] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [teramars]\n\t\t\t\n\t\t\t"                                  
    ## [10] "\n\t\t\t\n\t\t\t\t[情報] 喬治克隆尼自編自導新作《Suburbicon》排定獎季上映日期\n\t\t\t\n\t\t\t"
    ## [11] "\n\t\t\t\n\t\t\t\t[片單] 電影開頭快速介紹故事背景原由\n\t\t\t\n\t\t\t"                        
    ## [12] "\n\t\t\t\n\t\t\t\t[情報] 冰雪奇緣年底將推出雪寶大冒險短片\n\t\t\t\n\t\t\t"                    
    ## [13] "\n\t\t\t\n\t\t\t\t[問片] 一部教育片 學生答題競賽\n\t\t\t\n\t\t\t"                             
    ## [14] "\n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t"                               
    ## [15] "\n\t\t\t\n\t\t\t\t[極好雷] 【我和我的冠軍女兒】觀後感\n\t\t\t\n\t\t\t"                        
    ## [16] "\n\t\t\t\n\t\t\t\tRe: [閒聊] 搞不懂梁朝偉演技到底哪裡好\n\t\t\t\n\t\t\t"                      
    ## [17] "\n\t\t\t\n\t\t\t\t[  小雷] 美女與野獸的同性戀劇情在哪？\n\t\t\t\n\t\t\t"                      
    ## [18] "\n\t\t\t\n\t\t\t\t[好雷] 拆彈少年\n\t\t\t\n\t\t\t"                                            
    ## [19] "\n\t\t\t\n\t\t\t\tRe: [分享] CATCHPLAY 和 friDay 字幕的新外掛！\n\t\t\t\n\t\t\t"              
    ## [20] "\n\t\t\t\n\t\t\t\t[請益] 關於電影院外那些酷卡\n\t\t\t\n\t\t\t"

``` r
post_author3<-pttcontent3%>%html_nodes(".author")%>%html_text()
post_author3
```

    ##  [1] "sysstat"     "wataru"      "CatchPlay"   "-"           "huanglove"  
    ##  [6] "Kobe2630"    "pili"        "sthho"       "-"           "qpr322"     
    ## [11] "j31404"      "AnneofGreen" "swgun"       "BanJarvan4"  "loveyilin"  
    ## [16] "gidens"      "gpo"         "pp810207"    "tea2024"     "yuan2lee"

``` r
post_good3<-pttcontent3%>%html_nodes(".nrec")%>%html_text()
post_good3
```

    ##  [1] "1"  "20" "36" ""   "7"  "49" "22" "13" ""   "1"  "47" "34" ""   "37"
    ## [15] "14" "53" "26" "2"  ""   "7"

``` r
ptt4<-"https://www.ptt.cc/bbs/movie/index5277.html"
pttcontent4<-read_html(ptt4)
post_title4<-pttcontent4%>%html_nodes(".title")%>%html_text()
post_title4
```

    ##  [1] "\n\t\t\t\n\t\t\t\t[討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t"                     
    ##  [2] "\n\t\t\t\n\t\t\t\t[問片] 法國浪漫電影\n\t\t\t\n\t\t\t"                          
    ##  [3] "\n\t\t\t\n\t\t\t\t[好雷] 聲之形     改變與成長\n\t\t\t\n\t\t\t"                 
    ##  [4] "\n\t\t\t\n\t\t\t\t[片單]求懸疑驚悚片～  想被嚇\n\t\t\t\n\t\t\t"                 
    ##  [5] "\n\t\t\t\n\t\t\t\tRe: [討論] 攻殼機動隊 最終預告\n\t\t\t\n\t\t\t"               
    ##  [6] "\n\t\t\t\n\t\t\t\t[好雷]明天 我要和昨天的妳約會\n\t\t\t\n\t\t\t"                
    ##  [7] "\n\t\t\t\n\t\t\t\t[好雷] 聲之形 剎那被震撼了(物理\n\t\t\t\n\t\t\t"              
    ##  [8] "\n\t\t\t\n\t\t\t\t（轉貼）一部電影一杯酒──電影迷人生必去聖地\n\t\t\t\n\t\t\t"   
    ##  [9] "\n\t\t\t\n\t\t\t\t[選片] 二輪: 鋼鐵英雄 VS. 拆彈少年\n\t\t\t\n\t\t\t"           
    ## [10] "\n\t\t\t\n\t\t\t\t[新聞] 正義聯盟新預告獨缺XX？導演回應了(有雷)\n\t\t\t\n\t\t\t"
    ## [11] "\n\t\t\t\n\t\t\t\t[好雷] 記憶拼圖其實是部女性電影吧\n\t\t\t\n\t\t\t"            
    ## [12] "\n\t\t\t\n\t\t\t\t[負雷] 金剛骷髏島\n\t\t\t\n\t\t\t"                            
    ## [13] "\n\t\t\t\n\t\t\t\t[新聞] 「藍色小精靈3」藏彩蛋 致敬原作有驚喜\n\t\t\t\n\t\t\t"  
    ## [14] "\n\t\t\t\n\t\t\t\t[普雷] 《金剛戰士》救世主，94狂\n\t\t\t\n\t\t\t"              
    ## [15] "\n\t\t\t\n\t\t\t\t[討論] 是什麼時候開始預告也要預告？\n\t\t\t\n\t\t\t"          
    ## [16] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [rgsniper]\n\t\t\t\n\t\t\t"                    
    ## [17] "\n\t\t\t\n\t\t\t\t[好無雷]  金剛戰士\n\t\t\t\n\t\t\t"                           
    ## [18] "\n\t\t\t\n\t\t\t\t[問片] 為了一把雷射槍去救被綁架的爸爸(有雷)\n\t\t\t\n\t\t\t"  
    ## [19] "\n\t\t\t\n\t\t\t\t[新聞] 斷人陽具撕臉皮 黃秋生演完嚇到喊收山\n\t\t\t\n\t\t\t"   
    ## [20] "\n\t\t\t\n\t\t\t\tRe: [討論] 珍妮佛勞倫斯是不是過譽了？\n\t\t\t\n\t\t\t"

``` r
post_author4<-pttcontent4%>%html_nodes(".author")%>%html_text()
post_author4
```

    ##  [1] "jjt820716"    "qoowhite"     "wowbenny"     "ask90636"    
    ##  [5] "ADIMM"        "sa40000"      "chct0613"     "error046"    
    ##  [9] "searoar"      "sampsonlu919" "plutox"       "kiwidoit"    
    ## [13] "sony577"      "bestbamboo"   "h2030625"     "-"           
    ## [17] "rgsniper"     "ljfqq6120"    "conpo"        "mikiup0321"

``` r
post_good4<-pttcontent4%>%html_nodes(".nrec")%>%html_text()
post_good4
```

    ##  [1] "2"  "8"  "1"  "27" "5"  "8"  "6"  "4"  "25" "45" "1"  ""   "4"  "4" 
    ## [15] "25" ""   "2"  "3"  "10" "3"

``` r
ptt5<-"https://www.ptt.cc/bbs/movie/index5276.html"
pttcontent5<-read_html(ptt5)
post_title5<-pttcontent5%>%html_nodes(".title")%>%html_text()
post_title5
```

    ##  [1] "\n\t\t\t\n\t\t\t\t[請益] \"痞子英雄\"電影版會有第3集嗎?\n\t\t\t\n\t\t\t"                          
    ##  [2] "\n\t\t\t\n\t\t\t\t[好雷] 如果這個世界貓消失了 那我還算活著嗎?\n\t\t\t\n\t\t\t"                    
    ##  [3] "\n\t\t\t\n\t\t\t\t[普雷] 異星智慧 \n\t\t\t\n\t\t\t"                                               
    ##  [4] "\n\t\t\t\n\t\t\t\t[情報] 凱西、勞勃瑞福與西西史派克主演新片由福斯探照燈取得發行權\n\t\t\t\n\t\t\t"
    ##  [5] "\n\t\t\t\n\t\t\t\t[新聞] 韓導演朴贊郁獲佛羅倫斯文化藝術獎\n\t\t\t\n\t\t\t"                        
    ##  [6] "\n\t\t\t\n\t\t\t\t[贈票] 已贈出 攻殼機動隊 IMAX 3D\n\t\t\t\n\t\t\t"                               
    ##  [7] "\n\t\t\t\n\t\t\t\t[選片] 聲之形 vs 我和我的冠軍女兒\n\t\t\t\n\t\t\t"                              
    ##  [8] "\n\t\t\t\n\t\t\t\t[還不錯雷雷]異星智慧 \n\t\t\t\n\t\t\t"                                          
    ##  [9] "\n\t\t\t\n\t\t\t\t[新聞] 【電影版聲之形】票房破2000萬奪新片冠軍\n\t\t\t\n\t\t\t"                  
    ## [10] "\n\t\t\t\n\t\t\t\t[討論] 奇異博士1:41:47的地方\n\t\t\t\n\t\t\t"                                   
    ## [11] "\n\t\t\t\n\t\t\t\t[普雷] 可以更好的金剛戰士 \n\t\t\t\n\t\t\t"                                     
    ## [12] "\n\t\t\t\n\t\t\t\t[好雷] 神奇大隊長－狠狠撞上現實的理想 \n\t\t\t\n\t\t\t"                         
    ## [13] "\n\t\t\t\n\t\t\t\tRe: [請益] 普羅米修斯造物主為什麼要殺人類\n\t\t\t\n\t\t\t"                      
    ## [14] "\n\t\t\t\n\t\t\t\t[討論] 攻殼機動隊 最終預告\n\t\t\t\n\t\t\t"                                     
    ## [15] "\n\t\t\t\n\t\t\t\t[討論] 那些今年滿20歲的電影(三)完結\n\t\t\t\n\t\t\t"                            
    ## [16] "\n\t\t\t\n\t\t\t\t[請益] 我和我的冠軍女兒片尾一段話\n\t\t\t\n\t\t\t"                              
    ## [17] "\n\t\t\t\n\t\t\t\t[討論] 金爆內幕【內含雷】\n\t\t\t\n\t\t\t"                                      
    ## [18] "\n\t\t\t\n\t\t\t\t[好雷] 攻敵必救：觀眾即是玩家！ \n\t\t\t\n\t\t\t"                               
    ## [19] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [evenchang]\n\t\t\t\n\t\t\t"                                     
    ## [20] "\n\t\t\t\n\t\t\t\t[好雷] 看不見的客人 - 起了一身雞皮疙瘩\n\t\t\t\n\t\t\t"

``` r
post_author5<-pttcontent5%>%html_nodes(".author")%>%html_text()
post_author5
```

    ##  [1] "huanglove"    "allen911007"  "m19871006"    "qpr322"      
    ##  [5] "iam168888888" "lkhuang"      "samuel082608" "hydrant"     
    ##  [9] "kkaicd1"      "MgcnVanish"   "recycling"    "twoquarters" 
    ## [13] "liusim"       "arsl400"      "peter220"     "camaroYP"    
    ## [17] "jack1231"     "bird3258"     "-"            "coopermilk"

``` r
post_good5<-pttcontent5%>%html_nodes(".nrec")%>%html_text()
post_good5
```

    ##  [1] "14" "13" "3"  ""   "4"  "5"  "61" "4"  "6"  "41" "2"  "2"  ""   "14"
    ## [15] "4"  "2"  "1"  "5"  ""   "5"

``` r
ptt6<-"https://www.ptt.cc/bbs/movie/index5275.html"
pttcontent6<-read_html(ptt6)
post_title6<-pttcontent6%>%html_nodes(".title")%>%html_text()
post_title6
```

    ##  [1] "\n\t\t\t\n\t\t\t\t[好雷]金剛戰士 \n\t\t\t\n\t\t\t"                                    
    ##  [2] "\n\t\t\t\n\t\t\t\tFw: [閒聊] 聲之形二刷 心得（有雷）\n\t\t\t\n\t\t\t"                 
    ##  [3] "\n\t\t\t\n\t\t\t\t[贈票] 湯姆漢克斯大力推薦《衝突的一天》贈票\n\t\t\t\n\t\t\t"        
    ##  [4] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [psooolder]\n\t\t\t\n\t\t\t"                         
    ##  [5] "\n\t\t\t\n\t\t\t\t[好雷] 美女與野獸 1991 & 2017，場景設計\n\t\t\t\n\t\t\t"            
    ##  [6] "\n\t\t\t\n\t\t\t\t[討論] 短心得：關於迪士尼公主的數學題\n\t\t\t\n\t\t\t"              
    ##  [7] "\n\t\t\t\n\t\t\t\t[選片] 明天我要和昨天的你約會 vs我的冠軍女兒\n\t\t\t\n\t\t\t"       
    ##  [8] "\n\t\t\t\n\t\t\t\t[問片] 問一部日本片，關於合唱團的\n\t\t\t\n\t\t\t"                  
    ##  [9] "\n\t\t\t\n\t\t\t\t[討論] 艾瑪華森與湯姆漢克斯新片《直播風暴》相關資訊\n\t\t\t\n\t\t\t"
    ## [10] "\n\t\t\t\n\t\t\t\t[討論] 《樂高蝙蝠俠電影》東森洋片現在播放中\n\t\t\t\n\t\t\t"        
    ## [11] "\n\t\t\t\n\t\t\t\t[心得] 韓國電影《非常警探》收賄刑警VS販毒警官\n\t\t\t\n\t\t\t"      
    ## [12] "\n\t\t\t\n\t\t\t\t[好雷] 韓國電影《標靶》電影介紹與心得\n\t\t\t\n\t\t\t"              
    ## [13] "\n\t\t\t\n\t\t\t\t[問片] 問一部臥底電影的片名（有雷）\n\t\t\t\n\t\t\t"                
    ## [14] "\n\t\t\t\n\t\t\t\tFw: [閒聊] Ghost int the shell系列介紹影片\n\t\t\t\n\t\t\t"         
    ## [15] "\n\t\t\t\n\t\t\t\t[討論] 原本沒興趣但卻意外好看的電影\n\t\t\t\n\t\t\t"                
    ## [16] "\n\t\t\t\n\t\t\t\t[討論] 珍妮佛勞倫斯是不是過譽了？\n\t\t\t\n\t\t\t"                  
    ## [17] "\n\t\t\t\n\t\t\t\t[新聞] 《蜘蛛人：返校日》反派禿鷹新情報\n\t\t\t\n\t\t\t"            
    ## [18] "\n\t\t\t\n\t\t\t\t[請益] 出現過這種角色的電影\n\t\t\t\n\t\t\t"                        
    ## [19] "\n\t\t\t\n\t\t\t\t[問片] 一部日本片(科幻?) 殺戮都市\n\t\t\t\n\t\t\t"                  
    ## [20] "\n\t\t\t\n\t\t\t\t[翻譯] 10個得按下暫停才看得到的迪士尼動畫彩蛋\n\t\t\t\n\t\t\t"

``` r
post_author6<-pttcontent6%>%html_nodes(".author")%>%html_text()
post_author6
```

    ##  [1] "iamandre"    "gc9987"      "pelicula"    "-"           "mysmalllamb"
    ##  [6] "wu05k3"      "kenlin0105"  "exporn"      "swizzleyeh"  "amandawang" 
    ## [11] "KpopNote"    "KpopNote"    "laggy"       "Swampert"    "litann4"    
    ## [16] "g21l"        "qn123456"    "carotyao"    "a128296578"  "TVpotato"

``` r
post_good6<-pttcontent6%>%html_nodes(".nrec")%>%html_text()
post_good6
```

    ##  [1] "8"  "9"  "77" "36" "24" "6"  "40" "8"  "18" "7"  "4"  "1"  "1"  "2" 
    ## [15] "爆" "73" "14" "4"  "7"  "1"

``` r
ptt7<-"https://www.ptt.cc/bbs/movie/index5274.html"
pttcontent7<-read_html(ptt7)
post_title7<-pttcontent7%>%html_nodes(".title")%>%html_text()
post_title7
```

    ##  [1] "\n\t\t\t\n\t\t\t\tRe: [討論] 《正義聯盟》首支正式預告釋出\n\t\t\t\n\t\t\t"          
    ##  [2] "\n\t\t\t\n\t\t\t\tRe: [請益] 羅賓掛了嗎? after 自殺突擊隊..\n\t\t\t\n\t\t\t"        
    ##  [3] "\n\t\t\t\n\t\t\t\tRe: [贈票] 橫掃義大利金獎大導《媽媽教我愛的一切》\n\t\t\t\n\t\t\t"
    ##  [4] "\n\t\t\t\n\t\t\t\t[好雷] 金剛:骷髏島(不提景甜) \n\t\t\t\n\t\t\t"                    
    ##  [5] "\n\t\t\t\n\t\t\t\t[新聞] 神片開賣5分鐘內GG 《猜火車2》加場爭取\n\t\t\t\n\t\t\t"     
    ##  [6] "\n\t\t\t\n\t\t\t\t[請益] 女主角是壞人但討人喜歡的電影？\n\t\t\t\n\t\t\t"            
    ##  [7] "\n\t\t\t\n\t\t\t\t[問片] 在飛機上看到的一部片\n\t\t\t\n\t\t\t"                      
    ##  [8] "\n\t\t\t\n\t\t\t\t[  雷] 好雷的金剛戰士，慎入\n\t\t\t\n\t\t\t"                      
    ##  [9] "\n\t\t\t\n\t\t\t\tRe: [請益] 當初AI人工智慧為何不在前面收尾就好？\n\t\t\t\n\t\t\t"  
    ## [10] "\n\t\t\t\n\t\t\t\tFw: [閒聊] 聲之形 無雷觀後感\n\t\t\t\n\t\t\t"                     
    ## [11] "\n\t\t\t\n\t\t\t\t[贈票] 【玩命關頭8】北中南推文搶先看\n\t\t\t\n\t\t\t"             
    ## [12] "\n\t\t\t\n\t\t\t\t[好雷] 決戰異世界：弒血之戰 - 狼人 > 吸血鬼\n\t\t\t\n\t\t\t"      
    ## [13] "\n\t\t\t\n\t\t\t\t[無雷] 《我和我的冠軍女兒》不爆雷觀後感 \n\t\t\t\n\t\t\t"         
    ## [14] "\n\t\t\t\n\t\t\t\t〔分享〕《猜火車2》金馬奇幻加開四場！\n\t\t\t\n\t\t\t"            
    ## [15] "\n\t\t\t\n\t\t\t\t[好雷]  《七月與安生》充滿糾結的友誼情感\n\t\t\t\n\t\t\t"         
    ## [16] "\n\t\t\t\n\t\t\t\t[問片]農莊主人和姪女不倫情節的北歐片?\n\t\t\t\n\t\t\t"            
    ## [17] "\n\t\t\t\n\t\t\t\t(本文已被刪除) [an5607]\n\t\t\t\n\t\t\t"                          
    ## [18] "\n\t\t\t\n\t\t\t\tRe: [請益] 羅賓掛了嗎? after 自殺突擊隊..\n\t\t\t\n\t\t\t"        
    ## [19] "\n\t\t\t\n\t\t\t\t[普暖雷]《生日卡片》- 主役的人不唱悲歌\n\t\t\t\n\t\t\t"           
    ## [20] "\n\t\t\t\n\t\t\t\t[新聞] 景甜好棒 《金剛》中國開片大勝北美\n\t\t\t\n\t\t\t"

``` r
post_author7<-pttcontent7%>%html_nodes(".author")%>%html_text()
post_author7
```

    ##  [1] "yashiro"      "sunny1991225" "indiasosp"    "BF109Pilot"  
    ##  [5] "asd591922"    "lemon7242"    "justforfun90" "triff"       
    ##  [9] "sofc"         "a4040856"     "ChloeD"       "SuperSg"     
    ## [13] "lasor"        "black99kk"    "pattichiu"    "channel79"   
    ## [17] "-"            "alljerry04"   "jk10134"      "blaster"

``` r
post_good7<-pttcontent7%>%html_nodes(".nrec")%>%html_text()
post_good7
```

    ##  [1] "38" "14" "3"  "10" "6"  "80" "7"  "15" "9"  "5"  "爆" "6"  "5"  "17"
    ## [15] ""   "1"  ""   "19" ""   "3"

``` r
frame1<-data.frame(Title=c(post_title1),pushnum=c(post_good1),Author=c(post_author1))
frame1
```

    ##                                                                            Title
    ## 1              \n\t\t\t\n\t\t\t\t[情報] 我和我的冠軍女兒臺北票房\n\t\t\t\n\t\t\t
    ## 2   \n\t\t\t\n\t\t\t\t[新聞] 韓版不能說的秘密明年開拍 網友不買單\n\t\t\t\n\t\t\t
    ## 3   \n\t\t\t\n\t\t\t\t[新聞] 莊凱勛拍目擊者 認真相也許沒那麼重要\n\t\t\t\n\t\t\t
    ## 4 \n\t\t\t\n\t\t\t\t[普雷] 金剛戰士 Power Rangers-追的是一段青春\n\t\t\t\n\t\t\t
    ## 5        \n\t\t\t\n\t\t\t\t[問片] 找部年代久遠香港有紙紮人的鬼片\n\t\t\t\n\t\t\t
    ## 6                    \n\t\t\t\n\t\t\t\t[公告]《各式疑難雜症FAQ》\n\t\t\t\n\t\t\t
    ## 7       \n\t\t\t\n\t\t\t\t[公告] 板規！必看！｜好文推薦‧惡文檢舉\n\t\t\t\n\t\t\t
    ## 8  \n\t\t\t\n\t\t\t\t[贈票] 湯姆漢克斯大力推薦《衝突的一天》贈票\n\t\t\t\n\t\t\t
    ##   pushnum       Author
    ## 1       1 lovelandbird
    ## 2       3 iam168888888
    ## 3       5 iam168888888
    ## 4       2   practice24
    ## 5              xxshoxx
    ## 6      23  yunyun85106
    ## 7      爆     ericf129
    ## 8      爆     pelicula

``` r
frame2<-data.frame(Title=c(post_title2),pushnum=c(post_good2),Author=c(post_author2))
frame2
```

    ##                                                                                                Title
    ## 1                                     \n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t
    ## 2                                 \n\t\t\t\n\t\t\t\t[ 普雷]好像沒人看過的《斧視眈眈 \n\t\t\t\n\t\t\t
    ## 3                                     \n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t
    ## 4                           \n\t\t\t\n\t\t\t\t[大好雷] 我和我的冠軍女兒-近期最愛電影\n\t\t\t\n\t\t\t
    ## 5                                          \n\t\t\t\n\t\t\t\t[好雷] 看情懷的金剛戰士\n\t\t\t\n\t\t\t
    ## 6                                     \n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t
    ## 7                           \n\t\t\t\n\t\t\t\t[討論] 我和我的冠軍女兒 大女兒（有雷）\n\t\t\t\n\t\t\t
    ## 8                                    \n\t\t\t\n\t\t\t\t[選片] 本能寺大飯店vs金剛戰士\n\t\t\t\n\t\t\t
    ## 9                               \n\t\t\t\n\t\t\t\t[普雷] 聲之形-如果今天被80的是醜女\n\t\t\t\n\t\t\t
    ## 10                                   \n\t\t\t\n\t\t\t\t[討論] 試映形式及其所代表意義\n\t\t\t\n\t\t\t
    ## 11                                         \n\t\t\t\n\t\t\t\t[討論] 愛是您愛是我續集\n\t\t\t\n\t\t\t
    ## 12                   \n\t\t\t\n\t\t\t\t[新聞] 《八月》：人啊，你是否低下過高貴的頭顱\n\t\t\t\n\t\t\t
    ## 13                     \n\t\t\t\n\t\t\t\t[討論] 這幾年還有什麼值得推薦的好萊塢動作片\n\t\t\t\n\t\t\t
    ## 14 \n\t\t\t\n\t\t\t\t[情報] 傑克葛倫霍主演波士頓馬拉松爆炸案電影《Stronger》由獅門影\n\t\t\t\n\t\t\t
    ## 15                                  \n\t\t\t\n\t\t\t\t[討論] 攻殼機動隊 該看3D?或4D?\n\t\t\t\n\t\t\t
    ## 16                    \n\t\t\t\n\t\t\t\t[新聞] 《猜火車2》道具慈善拍賣　卑比坐牢用的\n\t\t\t\n\t\t\t
    ## 17                                    \n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t
    ## 18                                        \n\t\t\t\n\t\t\t\t[請益] 我和我的冠軍女兒 \n\t\t\t\n\t\t\t
    ## 19                                               \n\t\t\t\n\t\t\t\t[討論] 銀魂真人版\n\t\t\t\n\t\t\t
    ## 20                              \n\t\t\t\n\t\t\t\t[討論] Captain Underpants 首回預告\n\t\t\t\n\t\t\t
    ##    pushnum       Author
    ## 1        3   SQUAD12345
    ## 2          lunanightcat
    ## 3       10      t13thbc
    ## 4        4   loveponpon
    ## 5       11      amy3692
    ## 6       35     ckshchen
    ## 7        9  ilovepitaya
    ## 8       14    aff002377
    ## 9        8   newshooter
    ## 10       3   alljerry04
    ## 11      28    AceRocker
    ## 12       9       JackAC
    ## 13       7   MgcnVanish
    ## 14       7       qpr322
    ## 15      15       nardus
    ## 16       2     ourstage
    ## 17       6      linkcat
    ## 18      20        anher
    ## 19      53 KingKingCold
    ## 20       1     debb0128

``` r
frame3<-data.frame(Title=c(post_title3),pushnum=c(post_good3),Author=c(post_author3))
frame3
```

    ##                                                                                            Title
    ## 1             \n\t\t\t\n\t\t\t\tRe: [情報] 帝國戰神：巴霍巴利王 好萊塢電影台首播\n\t\t\t\n\t\t\t
    ## 2                       \n\t\t\t\n\t\t\t\t[新聞] 獅門影業或將拍攝5-7集金剛戰士！\n\t\t\t\n\t\t\t
    ## 3                  \n\t\t\t\n\t\t\t\t[新聞] 《金剛戰士》導演爆料續集將有經典角色\n\t\t\t\n\t\t\t
    ## 4                                    \n\t\t\t\n\t\t\t\t(本文已被刪除) [Kobe2630]\n\t\t\t\n\t\t\t
    ## 5              \n\t\t\t\n\t\t\t\t[新聞] 賀歲片王豬哥亮驚傳離世？經紀人指尚未證實\n\t\t\t\n\t\t\t
    ## 6                            \n\t\t\t\n\t\t\t\t[閒聊] 搞不懂梁朝偉演技到底哪裡好\n\t\t\t\n\t\t\t
    ## 7                \n\t\t\t\n\t\t\t\t[新聞] 美女與野獸奪北美台灣雙週冠軍有望出外傳\n\t\t\t\n\t\t\t
    ## 8                     \n\t\t\t\n\t\t\t\t[好雷] 美女與野獸 卡通與真人不一樣的地方\n\t\t\t\n\t\t\t
    ## 9                                    \n\t\t\t\n\t\t\t\t(本文已被刪除) [teramars]\n\t\t\t\n\t\t\t
    ## 10 \n\t\t\t\n\t\t\t\t[情報] 喬治克隆尼自編自導新作《Suburbicon》排定獎季上映日期\n\t\t\t\n\t\t\t
    ## 11                         \n\t\t\t\n\t\t\t\t[片單] 電影開頭快速介紹故事背景原由\n\t\t\t\n\t\t\t
    ## 12                     \n\t\t\t\n\t\t\t\t[情報] 冰雪奇緣年底將推出雪寶大冒險短片\n\t\t\t\n\t\t\t
    ## 13                              \n\t\t\t\n\t\t\t\t[問片] 一部教育片 學生答題競賽\n\t\t\t\n\t\t\t
    ## 14                                \n\t\t\t\n\t\t\t\tRe: [討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t
    ## 15                         \n\t\t\t\n\t\t\t\t[極好雷] 【我和我的冠軍女兒】觀後感\n\t\t\t\n\t\t\t
    ## 16                       \n\t\t\t\n\t\t\t\tRe: [閒聊] 搞不懂梁朝偉演技到底哪裡好\n\t\t\t\n\t\t\t
    ## 17                       \n\t\t\t\n\t\t\t\t[  小雷] 美女與野獸的同性戀劇情在哪？\n\t\t\t\n\t\t\t
    ## 18                                             \n\t\t\t\n\t\t\t\t[好雷] 拆彈少年\n\t\t\t\n\t\t\t
    ## 19               \n\t\t\t\n\t\t\t\tRe: [分享] CATCHPLAY 和 friDay 字幕的新外掛！\n\t\t\t\n\t\t\t
    ## 20                                 \n\t\t\t\n\t\t\t\t[請益] 關於電影院外那些酷卡\n\t\t\t\n\t\t\t
    ##    pushnum      Author
    ## 1        1     sysstat
    ## 2       20      wataru
    ## 3       36   CatchPlay
    ## 4                    -
    ## 5        7   huanglove
    ## 6       49    Kobe2630
    ## 7       22        pili
    ## 8       13       sthho
    ## 9                    -
    ## 10       1      qpr322
    ## 11      47      j31404
    ## 12      34 AnneofGreen
    ## 13               swgun
    ## 14      37  BanJarvan4
    ## 15      14   loveyilin
    ## 16      53      gidens
    ## 17      26         gpo
    ## 18       2    pp810207
    ## 19             tea2024
    ## 20       7    yuan2lee

``` r
frame4<-data.frame(Title=c(post_title4),pushnum=c(post_good4),Author=c(post_author4))
frame4
```

    ##                                                                              Title
    ## 1                       \n\t\t\t\n\t\t\t\t[討論] BVS終極版  很神啊\n\t\t\t\n\t\t\t
    ## 2                            \n\t\t\t\n\t\t\t\t[問片] 法國浪漫電影\n\t\t\t\n\t\t\t
    ## 3                   \n\t\t\t\n\t\t\t\t[好雷] 聲之形     改變與成長\n\t\t\t\n\t\t\t
    ## 4                   \n\t\t\t\n\t\t\t\t[片單]求懸疑驚悚片～  想被嚇\n\t\t\t\n\t\t\t
    ## 5                 \n\t\t\t\n\t\t\t\tRe: [討論] 攻殼機動隊 最終預告\n\t\t\t\n\t\t\t
    ## 6                  \n\t\t\t\n\t\t\t\t[好雷]明天 我要和昨天的妳約會\n\t\t\t\n\t\t\t
    ## 7                \n\t\t\t\n\t\t\t\t[好雷] 聲之形 剎那被震撼了(物理\n\t\t\t\n\t\t\t
    ## 8     \n\t\t\t\n\t\t\t\t（轉貼）一部電影一杯酒──電影迷人生必去聖地\n\t\t\t\n\t\t\t
    ## 9             \n\t\t\t\n\t\t\t\t[選片] 二輪: 鋼鐵英雄 VS. 拆彈少年\n\t\t\t\n\t\t\t
    ## 10 \n\t\t\t\n\t\t\t\t[新聞] 正義聯盟新預告獨缺XX？導演回應了(有雷)\n\t\t\t\n\t\t\t
    ## 11             \n\t\t\t\n\t\t\t\t[好雷] 記憶拼圖其實是部女性電影吧\n\t\t\t\n\t\t\t
    ## 12                             \n\t\t\t\n\t\t\t\t[負雷] 金剛骷髏島\n\t\t\t\n\t\t\t
    ## 13   \n\t\t\t\n\t\t\t\t[新聞] 「藍色小精靈3」藏彩蛋 致敬原作有驚喜\n\t\t\t\n\t\t\t
    ## 14               \n\t\t\t\n\t\t\t\t[普雷] 《金剛戰士》救世主，94狂\n\t\t\t\n\t\t\t
    ## 15           \n\t\t\t\n\t\t\t\t[討論] 是什麼時候開始預告也要預告？\n\t\t\t\n\t\t\t
    ## 16                     \n\t\t\t\n\t\t\t\t(本文已被刪除) [rgsniper]\n\t\t\t\n\t\t\t
    ## 17                            \n\t\t\t\n\t\t\t\t[好無雷]  金剛戰士\n\t\t\t\n\t\t\t
    ## 18   \n\t\t\t\n\t\t\t\t[問片] 為了一把雷射槍去救被綁架的爸爸(有雷)\n\t\t\t\n\t\t\t
    ## 19    \n\t\t\t\n\t\t\t\t[新聞] 斷人陽具撕臉皮 黃秋生演完嚇到喊收山\n\t\t\t\n\t\t\t
    ## 20         \n\t\t\t\n\t\t\t\tRe: [討論] 珍妮佛勞倫斯是不是過譽了？\n\t\t\t\n\t\t\t
    ##    pushnum       Author
    ## 1        2    jjt820716
    ## 2        8     qoowhite
    ## 3        1     wowbenny
    ## 4       27     ask90636
    ## 5        5        ADIMM
    ## 6        8      sa40000
    ## 7        6     chct0613
    ## 8        4     error046
    ## 9       25      searoar
    ## 10      45 sampsonlu919
    ## 11       1       plutox
    ## 12             kiwidoit
    ## 13       4      sony577
    ## 14       4   bestbamboo
    ## 15      25     h2030625
    ## 16                    -
    ## 17       2     rgsniper
    ## 18       3    ljfqq6120
    ## 19      10        conpo
    ## 20       3   mikiup0321

``` r
frame5<-data.frame(Title=c(post_title5),pushnum=c(post_good5),Author=c(post_author5))
frame5
```

    ##                                                                                                Title
    ## 1                              \n\t\t\t\n\t\t\t\t[請益] "痞子英雄"電影版會有第3集嗎?\n\t\t\t\n\t\t\t
    ## 2                      \n\t\t\t\n\t\t\t\t[好雷] 如果這個世界貓消失了 那我還算活著嗎?\n\t\t\t\n\t\t\t
    ## 3                                                 \n\t\t\t\n\t\t\t\t[普雷] 異星智慧 \n\t\t\t\n\t\t\t
    ## 4  \n\t\t\t\n\t\t\t\t[情報] 凱西、勞勃瑞福與西西史派克主演新片由福斯探照燈取得發行權\n\t\t\t\n\t\t\t
    ## 5                          \n\t\t\t\n\t\t\t\t[新聞] 韓導演朴贊郁獲佛羅倫斯文化藝術獎\n\t\t\t\n\t\t\t
    ## 6                                 \n\t\t\t\n\t\t\t\t[贈票] 已贈出 攻殼機動隊 IMAX 3D\n\t\t\t\n\t\t\t
    ## 7                                \n\t\t\t\n\t\t\t\t[選片] 聲之形 vs 我和我的冠軍女兒\n\t\t\t\n\t\t\t
    ## 8                                            \n\t\t\t\n\t\t\t\t[還不錯雷雷]異星智慧 \n\t\t\t\n\t\t\t
    ## 9                    \n\t\t\t\n\t\t\t\t[新聞] 【電影版聲之形】票房破2000萬奪新片冠軍\n\t\t\t\n\t\t\t
    ## 10                                    \n\t\t\t\n\t\t\t\t[討論] 奇異博士1:41:47的地方\n\t\t\t\n\t\t\t
    ## 11                                      \n\t\t\t\n\t\t\t\t[普雷] 可以更好的金剛戰士 \n\t\t\t\n\t\t\t
    ## 12                          \n\t\t\t\n\t\t\t\t[好雷] 神奇大隊長－狠狠撞上現實的理想 \n\t\t\t\n\t\t\t
    ## 13                       \n\t\t\t\n\t\t\t\tRe: [請益] 普羅米修斯造物主為什麼要殺人類\n\t\t\t\n\t\t\t
    ## 14                                      \n\t\t\t\n\t\t\t\t[討論] 攻殼機動隊 最終預告\n\t\t\t\n\t\t\t
    ## 15                             \n\t\t\t\n\t\t\t\t[討論] 那些今年滿20歲的電影(三)完結\n\t\t\t\n\t\t\t
    ## 16                               \n\t\t\t\n\t\t\t\t[請益] 我和我的冠軍女兒片尾一段話\n\t\t\t\n\t\t\t
    ## 17                                       \n\t\t\t\n\t\t\t\t[討論] 金爆內幕【內含雷】\n\t\t\t\n\t\t\t
    ## 18                                \n\t\t\t\n\t\t\t\t[好雷] 攻敵必救：觀眾即是玩家！ \n\t\t\t\n\t\t\t
    ## 19                                      \n\t\t\t\n\t\t\t\t(本文已被刪除) [evenchang]\n\t\t\t\n\t\t\t
    ## 20                          \n\t\t\t\n\t\t\t\t[好雷] 看不見的客人 - 起了一身雞皮疙瘩\n\t\t\t\n\t\t\t
    ##    pushnum       Author
    ## 1       14    huanglove
    ## 2       13  allen911007
    ## 3        3    m19871006
    ## 4                qpr322
    ## 5        4 iam168888888
    ## 6        5      lkhuang
    ## 7       61 samuel082608
    ## 8        4      hydrant
    ## 9        6      kkaicd1
    ## 10      41   MgcnVanish
    ## 11       2    recycling
    ## 12       2  twoquarters
    ## 13               liusim
    ## 14      14      arsl400
    ## 15       4     peter220
    ## 16       2     camaroYP
    ## 17       1     jack1231
    ## 18       5     bird3258
    ## 19                    -
    ## 20       5   coopermilk

``` r
frame6<-data.frame(Title=c(post_title6),pushnum=c(post_good6),Author=c(post_author6))
frame6
```

    ##                                                                                    Title
    ## 1                                      \n\t\t\t\n\t\t\t\t[好雷]金剛戰士 \n\t\t\t\n\t\t\t
    ## 2                   \n\t\t\t\n\t\t\t\tFw: [閒聊] 聲之形二刷 心得（有雷）\n\t\t\t\n\t\t\t
    ## 3          \n\t\t\t\n\t\t\t\t[贈票] 湯姆漢克斯大力推薦《衝突的一天》贈票\n\t\t\t\n\t\t\t
    ## 4                           \n\t\t\t\n\t\t\t\t(本文已被刪除) [psooolder]\n\t\t\t\n\t\t\t
    ## 5              \n\t\t\t\n\t\t\t\t[好雷] 美女與野獸 1991 & 2017，場景設計\n\t\t\t\n\t\t\t
    ## 6                \n\t\t\t\n\t\t\t\t[討論] 短心得：關於迪士尼公主的數學題\n\t\t\t\n\t\t\t
    ## 7         \n\t\t\t\n\t\t\t\t[選片] 明天我要和昨天的你約會 vs我的冠軍女兒\n\t\t\t\n\t\t\t
    ## 8                    \n\t\t\t\n\t\t\t\t[問片] 問一部日本片，關於合唱團的\n\t\t\t\n\t\t\t
    ## 9  \n\t\t\t\n\t\t\t\t[討論] 艾瑪華森與湯姆漢克斯新片《直播風暴》相關資訊\n\t\t\t\n\t\t\t
    ## 10         \n\t\t\t\n\t\t\t\t[討論] 《樂高蝙蝠俠電影》東森洋片現在播放中\n\t\t\t\n\t\t\t
    ## 11       \n\t\t\t\n\t\t\t\t[心得] 韓國電影《非常警探》收賄刑警VS販毒警官\n\t\t\t\n\t\t\t
    ## 12               \n\t\t\t\n\t\t\t\t[好雷] 韓國電影《標靶》電影介紹與心得\n\t\t\t\n\t\t\t
    ## 13                 \n\t\t\t\n\t\t\t\t[問片] 問一部臥底電影的片名（有雷）\n\t\t\t\n\t\t\t
    ## 14          \n\t\t\t\n\t\t\t\tFw: [閒聊] Ghost int the shell系列介紹影片\n\t\t\t\n\t\t\t
    ## 15                 \n\t\t\t\n\t\t\t\t[討論] 原本沒興趣但卻意外好看的電影\n\t\t\t\n\t\t\t
    ## 16                   \n\t\t\t\n\t\t\t\t[討論] 珍妮佛勞倫斯是不是過譽了？\n\t\t\t\n\t\t\t
    ## 17             \n\t\t\t\n\t\t\t\t[新聞] 《蜘蛛人：返校日》反派禿鷹新情報\n\t\t\t\n\t\t\t
    ## 18                         \n\t\t\t\n\t\t\t\t[請益] 出現過這種角色的電影\n\t\t\t\n\t\t\t
    ## 19                   \n\t\t\t\n\t\t\t\t[問片] 一部日本片(科幻?) 殺戮都市\n\t\t\t\n\t\t\t
    ## 20       \n\t\t\t\n\t\t\t\t[翻譯] 10個得按下暫停才看得到的迪士尼動畫彩蛋\n\t\t\t\n\t\t\t
    ##    pushnum      Author
    ## 1        8    iamandre
    ## 2        9      gc9987
    ## 3       77    pelicula
    ## 4       36           -
    ## 5       24 mysmalllamb
    ## 6        6      wu05k3
    ## 7       40  kenlin0105
    ## 8        8      exporn
    ## 9       18  swizzleyeh
    ## 10       7  amandawang
    ## 11       4    KpopNote
    ## 12       1    KpopNote
    ## 13       1       laggy
    ## 14       2    Swampert
    ## 15      爆     litann4
    ## 16      73        g21l
    ## 17      14    qn123456
    ## 18       4    carotyao
    ## 19       7  a128296578
    ## 20       1    TVpotato

``` r
frame7<-data.frame(Title=c(post_title7),pushnum=c(post_good7),Author=c(post_author7))
frame7
```

    ##                                                                                  Title
    ## 1            \n\t\t\t\n\t\t\t\tRe: [討論] 《正義聯盟》首支正式預告釋出\n\t\t\t\n\t\t\t
    ## 2          \n\t\t\t\n\t\t\t\tRe: [請益] 羅賓掛了嗎? after 自殺突擊隊..\n\t\t\t\n\t\t\t
    ## 3  \n\t\t\t\n\t\t\t\tRe: [贈票] 橫掃義大利金獎大導《媽媽教我愛的一切》\n\t\t\t\n\t\t\t
    ## 4                      \n\t\t\t\n\t\t\t\t[好雷] 金剛:骷髏島(不提景甜) \n\t\t\t\n\t\t\t
    ## 5       \n\t\t\t\n\t\t\t\t[新聞] 神片開賣5分鐘內GG 《猜火車2》加場爭取\n\t\t\t\n\t\t\t
    ## 6              \n\t\t\t\n\t\t\t\t[請益] 女主角是壞人但討人喜歡的電影？\n\t\t\t\n\t\t\t
    ## 7                        \n\t\t\t\n\t\t\t\t[問片] 在飛機上看到的一部片\n\t\t\t\n\t\t\t
    ## 8                        \n\t\t\t\n\t\t\t\t[  雷] 好雷的金剛戰士，慎入\n\t\t\t\n\t\t\t
    ## 9    \n\t\t\t\n\t\t\t\tRe: [請益] 當初AI人工智慧為何不在前面收尾就好？\n\t\t\t\n\t\t\t
    ## 10                      \n\t\t\t\n\t\t\t\tFw: [閒聊] 聲之形 無雷觀後感\n\t\t\t\n\t\t\t
    ## 11              \n\t\t\t\n\t\t\t\t[贈票] 【玩命關頭8】北中南推文搶先看\n\t\t\t\n\t\t\t
    ## 12       \n\t\t\t\n\t\t\t\t[好雷] 決戰異世界：弒血之戰 - 狼人 > 吸血鬼\n\t\t\t\n\t\t\t
    ## 13          \n\t\t\t\n\t\t\t\t[無雷] 《我和我的冠軍女兒》不爆雷觀後感 \n\t\t\t\n\t\t\t
    ## 14             \n\t\t\t\n\t\t\t\t〔分享〕《猜火車2》金馬奇幻加開四場！\n\t\t\t\n\t\t\t
    ## 15          \n\t\t\t\n\t\t\t\t[好雷]  《七月與安生》充滿糾結的友誼情感\n\t\t\t\n\t\t\t
    ## 16             \n\t\t\t\n\t\t\t\t[問片]農莊主人和姪女不倫情節的北歐片?\n\t\t\t\n\t\t\t
    ## 17                           \n\t\t\t\n\t\t\t\t(本文已被刪除) [an5607]\n\t\t\t\n\t\t\t
    ## 18         \n\t\t\t\n\t\t\t\tRe: [請益] 羅賓掛了嗎? after 自殺突擊隊..\n\t\t\t\n\t\t\t
    ## 19            \n\t\t\t\n\t\t\t\t[普暖雷]《生日卡片》- 主役的人不唱悲歌\n\t\t\t\n\t\t\t
    ## 20          \n\t\t\t\n\t\t\t\t[新聞] 景甜好棒 《金剛》中國開片大勝北美\n\t\t\t\n\t\t\t
    ##    pushnum       Author
    ## 1       38      yashiro
    ## 2       14 sunny1991225
    ## 3        3    indiasosp
    ## 4       10   BF109Pilot
    ## 5        6    asd591922
    ## 6       80    lemon7242
    ## 7        7 justforfun90
    ## 8       15        triff
    ## 9        9         sofc
    ## 10       5     a4040856
    ## 11      爆       ChloeD
    ## 12       6      SuperSg
    ## 13       5        lasor
    ## 14      17    black99kk
    ## 15            pattichiu
    ## 16       1    channel79
    ## 17                    -
    ## 18      19   alljerry04
    ## 19              jk10134
    ## 20       3      blaster

``` r
dataframeAll<-rbind(frame1,frame2,frame3,frame4,frame5,frame6,frame7)
```

爬蟲結果呈現
------------

``` r
knitr::kable(dataframeAll[1:100,c("Title","pushnum","Author")])
```

| Title                                                             | pushnum | Author       |
|:------------------------------------------------------------------|:--------|:-------------|
| \[情報\] 我和我的冠軍女兒臺北票房                                 | 1       | lovelandbird |
| \[新聞\] 韓版不能說的秘密明年開拍 網友不買單                      | 3       | iam168888888 |
| \[新聞\] 莊凱勛拍目擊者 認真相也許沒那麼重要                      | 5       | iam168888888 |
| \[普雷\] 金剛戰士 Power Rangers-追的是一段青春                    | 2       | practice24   |
| \[問片\] 找部年代久遠香港有紙紮人的鬼片                           |         | xxshoxx      |
| \[公告\]《各式疑難雜症FAQ》                                       | 23      | yunyun85106  |
| \[公告\] 板規！必看！｜好文推薦‧惡文檢舉                          | 爆      | ericf129     |
| \[贈票\] 湯姆漢克斯大力推薦《衝突的一天》贈票                     | 爆      | pelicula     |
| Re: \[討論\] BVS終極版 很神啊                                     | 3       | SQUAD12345   |
| \[ 普雷\]好像沒人看過的《斧視眈眈                                 |         | lunanightcat |
| Re: \[討論\] BVS終極版 很神啊                                     | 10      | t13thbc      |
| \[大好雷\] 我和我的冠軍女兒-近期最愛電影                          | 4       | loveponpon   |
| \[好雷\] 看情懷的金剛戰士                                         | 11      | amy3692      |
| Re: \[討論\] BVS終極版 很神啊                                     | 35      | ckshchen     |
| \[討論\] 我和我的冠軍女兒 大女兒（有雷）                          | 9       | ilovepitaya  |
| \[選片\] 本能寺大飯店vs金剛戰士                                   | 14      | aff002377    |
| \[普雷\] 聲之形-如果今天被80的是醜女                              | 8       | newshooter   |
| \[討論\] 試映形式及其所代表意義                                   | 3       | alljerry04   |
| \[討論\] 愛是您愛是我續集                                         | 28      | AceRocker    |
| \[新聞\] 《八月》：人啊，你是否低下過高貴的頭顱                   | 9       | JackAC       |
| \[討論\] 這幾年還有什麼值得推薦的好萊塢動作片                     | 7       | MgcnVanish   |
| \[情報\] 傑克葛倫霍主演波士頓馬拉松爆炸案電影《Stronger》由獅門影 | 7       | qpr322       |
| \[討論\] 攻殼機動隊 該看3D?或4D?                                  | 15      | nardus       |
| \[新聞\] 《猜火車2》道具慈善拍賣　卑比坐牢用的                    | 2       | ourstage     |
| Re: \[討論\] BVS終極版 很神啊                                     | 6       | linkcat      |
| \[請益\] 我和我的冠軍女兒                                         | 20      | anher        |
| \[討論\] 銀魂真人版                                               | 53      | KingKingCold |
| \[討論\] Captain Underpants 首回預告                              | 1       | debb0128     |
| Re: \[情報\] 帝國戰神：巴霍巴利王 好萊塢電影台首播                | 1       | sysstat      |
| \[新聞\] 獅門影業或將拍攝5-7集金剛戰士！                          | 20      | wataru       |
| \[新聞\] 《金剛戰士》導演爆料續集將有經典角色                     | 36      | CatchPlay    |
| (本文已被刪除) \[Kobe2630\]                                       |         | -            |
| \[新聞\] 賀歲片王豬哥亮驚傳離世？經紀人指尚未證實                 | 7       | huanglove    |
| \[閒聊\] 搞不懂梁朝偉演技到底哪裡好                               | 49      | Kobe2630     |
| \[新聞\] 美女與野獸奪北美台灣雙週冠軍有望出外傳                   | 22      | pili         |
| \[好雷\] 美女與野獸 卡通與真人不一樣的地方                        | 13      | sthho        |
| (本文已被刪除) \[teramars\]                                       |         | -            |
| \[情報\] 喬治克隆尼自編自導新作《Suburbicon》排定獎季上映日期     | 1       | qpr322       |
| \[片單\] 電影開頭快速介紹故事背景原由                             | 47      | j31404       |
| \[情報\] 冰雪奇緣年底將推出雪寶大冒險短片                         | 34      | AnneofGreen  |
| \[問片\] 一部教育片 學生答題競賽                                  |         | swgun        |
| Re: \[討論\] BVS終極版 很神啊                                     | 37      | BanJarvan4   |
| \[極好雷\] 【我和我的冠軍女兒】觀後感                             | 14      | loveyilin    |
| Re: \[閒聊\] 搞不懂梁朝偉演技到底哪裡好                           | 53      | gidens       |
| \[ 小雷\] 美女與野獸的同性戀劇情在哪？                            | 26      | gpo          |
| \[好雷\] 拆彈少年                                                 | 2       | pp810207     |
| Re: \[分享\] CATCHPLAY 和 friDay 字幕的新外掛！                   |         | tea2024      |
| \[請益\] 關於電影院外那些酷卡                                     | 7       | yuan2lee     |
| \[討論\] BVS終極版 很神啊                                         | 2       | jjt820716    |
| \[問片\] 法國浪漫電影                                             | 8       | qoowhite     |
| \[好雷\] 聲之形 改變與成長                                        | 1       | wowbenny     |
| \[片單\]求懸疑驚悚片～ 想被嚇                                     | 27      | ask90636     |
| Re: \[討論\] 攻殼機動隊 最終預告                                  | 5       | ADIMM        |
| \[好雷\]明天 我要和昨天的妳約會                                   | 8       | sa40000      |
| \[好雷\] 聲之形 剎那被震撼了(物理                                 | 6       | chct0613     |
| （轉貼）一部電影一杯酒──電影迷人生必去聖地                        | 4       | error046     |
| \[選片\] 二輪: 鋼鐵英雄 VS. 拆彈少年                              | 25      | searoar      |
| \[新聞\] 正義聯盟新預告獨缺XX？導演回應了(有雷)                   | 45      | sampsonlu919 |
| \[好雷\] 記憶拼圖其實是部女性電影吧                               | 1       | plutox       |
| \[負雷\] 金剛骷髏島                                               |         | kiwidoit     |
| \[新聞\] 「藍色小精靈3」藏彩蛋 致敬原作有驚喜                     | 4       | sony577      |
| \[普雷\] 《金剛戰士》救世主，94狂                                 | 4       | bestbamboo   |
| \[討論\] 是什麼時候開始預告也要預告？                             | 25      | h2030625     |
| (本文已被刪除) \[rgsniper\]                                       |         | -            |
| \[好無雷\] 金剛戰士                                               | 2       | rgsniper     |
| \[問片\] 為了一把雷射槍去救被綁架的爸爸(有雷)                     | 3       | ljfqq6120    |
| \[新聞\] 斷人陽具撕臉皮 黃秋生演完嚇到喊收山                      | 10      | conpo        |
| Re: \[討論\] 珍妮佛勞倫斯是不是過譽了？                           | 3       | mikiup0321   |
| \[請益\] "痞子英雄"電影版會有第3集嗎?                             | 14      | huanglove    |
| \[好雷\] 如果這個世界貓消失了 那我還算活著嗎?                     | 13      | allen911007  |
| \[普雷\] 異星智慧                                                 | 3       | m19871006    |
| \[情報\] 凱西、勞勃瑞福與西西史派克主演新片由福斯探照燈取得發行權 |         | qpr322       |
| \[新聞\] 韓導演朴贊郁獲佛羅倫斯文化藝術獎                         | 4       | iam168888888 |
| \[贈票\] 已贈出 攻殼機動隊 IMAX 3D                                | 5       | lkhuang      |
| \[選片\] 聲之形 vs 我和我的冠軍女兒                               | 61      | samuel082608 |
| \[還不錯雷雷\]異星智慧                                            | 4       | hydrant      |
| \[新聞\] 【電影版聲之形】票房破2000萬奪新片冠軍                   | 6       | kkaicd1      |
| \[討論\] 奇異博士1:41:47的地方                                    | 41      | MgcnVanish   |
| \[普雷\] 可以更好的金剛戰士                                       | 2       | recycling    |
| \[好雷\] 神奇大隊長－狠狠撞上現實的理想                           | 2       | twoquarters  |
| Re: \[請益\] 普羅米修斯造物主為什麼要殺人類                       |         | liusim       |
| \[討論\] 攻殼機動隊 最終預告                                      | 14      | arsl400      |
| \[討論\] 那些今年滿20歲的電影(三)完結                             | 4       | peter220     |
| \[請益\] 我和我的冠軍女兒片尾一段話                               | 2       | camaroYP     |
| \[討論\] 金爆內幕【內含雷】                                       | 1       | jack1231     |
| \[好雷\] 攻敵必救：觀眾即是玩家！                                 | 5       | bird3258     |
| (本文已被刪除) \[evenchang\]                                      |         | -            |
| \[好雷\] 看不見的客人 - 起了一身雞皮疙瘩                          | 5       | coopermilk   |
| \[好雷\]金剛戰士                                                  | 8       | iamandre     |
| Fw: \[閒聊\] 聲之形二刷 心得（有雷）                              | 9       | gc9987       |
| \[贈票\] 湯姆漢克斯大力推薦《衝突的一天》贈票                     | 77      | pelicula     |
| (本文已被刪除) \[psooolder\]                                      | 36      | -            |
| \[好雷\] 美女與野獸 1991 & 2017，場景設計                         | 24      | mysmalllamb  |
| \[討論\] 短心得：關於迪士尼公主的數學題                           | 6       | wu05k3       |
| \[選片\] 明天我要和昨天的你約會 vs我的冠軍女兒                    | 40      | kenlin0105   |
| \[問片\] 問一部日本片，關於合唱團的                               | 8       | exporn       |
| \[討論\] 艾瑪華森與湯姆漢克斯新片《直播風暴》相關資訊             | 18      | swizzleyeh   |
| \[討論\] 《樂高蝙蝠俠電影》東森洋片現在播放中                     | 7       | amandawang   |
| \[心得\] 韓國電影《非常警探》收賄刑警VS販毒警官                   | 4       | KpopNote     |
| \[好雷\] 韓國電影《標靶》電影介紹與心得                           | 1       | KpopNote     |

解釋爬蟲結果
------------

``` r
dim(dataframeAll)
```

    ## [1] 128   3

抓出127筆觀察值，3個欄位

``` r
table(dataframeAll$Author)
```

    ## 
    ##     ericf129 iam168888888 lovelandbird     pelicula   practice24 
    ##            1            3            1            2            1 
    ##      xxshoxx  yunyun85106    AceRocker    aff002377   alljerry04 
    ##            1            1            1            1            2 
    ##      amy3692        anher     ckshchen     debb0128  ilovepitaya 
    ##            1            1            1            1            1 
    ##       JackAC KingKingCold      linkcat   loveponpon lunanightcat 
    ##            1            1            1            1            1 
    ##   MgcnVanish       nardus   newshooter     ourstage       qpr322 
    ##            2            1            1            1            3 
    ##   SQUAD12345      t13thbc            -  AnneofGreen   BanJarvan4 
    ##            1            1            6            1            1 
    ##    CatchPlay       gidens          gpo    huanglove       j31404 
    ##            1            1            1            2            1 
    ##     Kobe2630    loveyilin         pili     pp810207        sthho 
    ##            1            1            1            1            1 
    ##        swgun      sysstat      tea2024       wataru     yuan2lee 
    ##            1            1            1            1            1 
    ##        ADIMM     ask90636   bestbamboo     chct0613        conpo 
    ##            1            1            1            1            1 
    ##     error046     h2030625    jjt820716     kiwidoit    ljfqq6120 
    ##            1            1            1            1            1 
    ##   mikiup0321       plutox     qoowhite     rgsniper      sa40000 
    ##            1            1            1            1            1 
    ## sampsonlu919      searoar      sony577     wowbenny  allen911007 
    ##            1            1            1            1            1 
    ##      arsl400     bird3258     camaroYP   coopermilk      hydrant 
    ##            1            1            1            1            1 
    ##     jack1231      kkaicd1       liusim      lkhuang    m19871006 
    ##            1            1            1            1            1 
    ##     peter220    recycling samuel082608  twoquarters   a128296578 
    ##            1            1            1            1            1 
    ##   amandawang     carotyao       exporn         g21l       gc9987 
    ##            1            1            1            1            1 
    ##     iamandre   kenlin0105     KpopNote        laggy      litann4 
    ##            1            1            2            1            1 
    ##  mysmalllamb     qn123456     Swampert   swizzleyeh     TVpotato 
    ##            1            1            1            1            1 
    ##       wu05k3     a4040856    asd591922   BF109Pilot    black99kk 
    ##            1            1            1            1            1 
    ##      blaster    channel79       ChloeD    indiasosp      jk10134 
    ##            1            1            1            1            1 
    ## justforfun90        lasor    lemon7242    pattichiu         sofc 
    ##            1            1            1            1            1 
    ## sunny1991225      SuperSg        triff      yashiro 
    ##            1            1            1            1

作者qpr322、iam168888888各有3篇po文

原來R的表格整理出來那麼好看啊!
