# xor
```javascript
seed = 0;
function stringHash(str,base) {
  let hash = 5381;
  for (let i = 0; i < str.length; i++) {
    hash = (hash * base) ^ str.charCodeAt(i);
  }
  return hash >>> 0; 
}
function seededRandom() {
    seed = (seed * 9301 + 49297) % 233280;
    return seed / 233280;
}
function crypto_xor(key,data){
    if(typeof key !="string") key = String.fromCharCode.apply(null,key);
    seed = stringHash(key,33) + stringHash(key,31) / 7   + 0.1000000007;
    for(var i = 0;i < data.length;i++){
       data[i]^=seededRandom()*256;
    }
    return data
}
```
