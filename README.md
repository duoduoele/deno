//和node的cryptojs使用方法完全一样，其实就是crypto-js

import CryptoJS from 'https://deno.land/x/cryptojs@v1.0.2/cryptojs.js';

//md5
function getMD5(str){
    return CryptoJS.MD5(str).toString();
};

//aes-加密
function AES_Encrypt(word,key) {
    key = CryptoJS.enc.Hex.parse(key);
    let srcs = CryptoJS.enc.Utf8.parse(word);
    let encrypted = CryptoJS.AES.encrypt(srcs, key, {
        mode: CryptoJS.mode.ECB,
        padding: CryptoJS.pad.Pkcs7,
        iv:''
    });
    return CryptoJS.enc.Hex.stringify(CryptoJS.enc.Base64.parse(encrypted.toString()));
};
//aes-解密
function AES_Decrypt(word,key) {
    key = CryptoJS.enc.Hex.parse(key);
    let srcs = CryptoJS.enc.Base64.stringify(CryptoJS.enc.Hex.parse(word));
    let decrypt = CryptoJS.AES.decrypt(srcs, key, {
        mode: CryptoJS.mode.ECB,
        padding: CryptoJS.pad.Pkcs7,
        iv:""
    });
    return decrypt.toString(CryptoJS.enc.Utf8);
};

//des-加密
function encrypt3des(data,desKey) {
    let key = CryptoJS.enc.Utf8.parse(desKey);
    let dataHex = CryptoJS.enc.Utf8.parse(data);
    let encrypted = CryptoJS.TripleDES.encrypt(dataHex, key, {
        iv: '',
        mode: CryptoJS.mode.ECB,
        padding: CryptoJS.pad.Pkcs7
    })
    let str = encrypted.ciphertext.toString(CryptoJS.enc.Base64)
    return str
}
//des-解密
function decrypt3des(data,desKey) {
    let key = CryptoJS.enc.Utf8.parse(desKey);
    let decrypt = CryptoJS.TripleDES.decrypt(data, key, {
        iv: '',
        mode: CryptoJS.mode.ECB,
        padding: CryptoJS.pad.Pkcs7
    })
    let decryptedStr = decrypt.toString(CryptoJS.enc.Utf8)
    return decryptedStr.toString()
}
