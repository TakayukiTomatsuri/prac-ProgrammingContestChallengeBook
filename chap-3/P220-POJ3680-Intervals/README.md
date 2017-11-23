# P220 PJ3680 Intervals
P199 minimumFlowでも使った、ポテンシャルを導入し負のコストを持つ辺があってもダイクストラ法が使えるようにしたアルゴリズムを用います。  
珍しいことに蟻本の解説で理解できたのであまり説明しません。  

    
区間として  
(a, b, w) = {(5,8, 10), (4,5, 2), (2,3, 9)}  
が与えられたとします。  
  
このaとbたちを一緒にしてソートし、重複を除きます。すると{2,3,4,5,8}になります。  
これらをノードとし、ノードインデックス0,  ..., 4に対応させ、こいつらを座標ノードと呼ぶことにします。  
  
ソースノードをsとし、ノードインデックスを5にします。  
シンクノードをtとし、ノードインデックスを6とします。  
  
sから、座標ノードの一番インデックスの小さいものに、容量K、コスト0の辺を張ります。
座標ノードの一番インデックスの大きいものから、tへ、容量K、コスト0の辺を張ります。  
そのあと、座標ノード間で、容量無限、コストは0の辺を張ります。このときは、インデックス0から1、1から2,3から4,...という風に張ります。  
そして、与えられた区間に対応するノードからノードへ、容量が1で、コストが(区間の重み*-1)の辺を張ります。  
たとえば、区間(5,8, 10)なら、座標5に対応する、インデックス3のノードから、座標8に対応する、インデックス4のノードに、容量1、コスト-10の辺を張ります。  
(コストがマイナスになるのは、最小費用流のアルゴリズムで答えを求めるためです。)  
  
そして、sからtへ流量がKの最小費用流を流すと、そのコストは求めたかった、区間重み(コスト)の和の最大値の符号を反転したものとなっています。  


#  参考
[ベルマンフォード法](https://qiita.com/intatonix/items/8a50556697206ee89bcd)
[フローの話。蟻本のはdist(s,v)をh(v)に積算していくとか書いてある] (https://gist.github.com/satos---jp/711c056cb63af7fbccb569f98a086b06)
[これも同上]https://www.slideshare.net/Drafaer/kmc-advanced-3)