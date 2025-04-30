
<!-- -->

```
import CryptoJS from 'https://deno.land/x/cryptojs@v1.0.7/cryptojs.js';

// CryptoJS.MD5('message').toString();
// CryptoJS.SHA256('message').toString();

// const hmac = CryptoJS.HmacSHA256('message', 'secret').toString(CryptoJS.enc.Hex);
// console.log('HMAC-SHA256 结果:', hmac);

// AES-encrypt
function encryptAES(text){
	let key = CryptoJS.enc.Utf8.parse('0123456789abcdef'); // 16字节密钥
	let iv = CryptoJS.enc.Utf8.parse('abcdef0123456789'); // 16字节偏移量
	const encrypted = CryptoJS.AES.encrypt(text, key, {
	    mode: CryptoJS.mode.CBC, // 加密模式
	    padding: CryptoJS.pad.Pkcs7, // 填充方式
	    iv,
	});
	return encrypted.toString();
};
// AES-decrypt
function decryptAES(text){
	let key = CryptoJS.enc.Utf8.parse('0123456789abcdef'); // 16字节密钥
	let iv = CryptoJS.enc.Utf8.parse('abcdef0123456789'); // 16字节偏移量
	const decrypted = CryptoJS.AES.decrypt(text, key, {
	    mode: CryptoJS.mode.CBC, // 加密模式
	    padding: CryptoJS.pad.Pkcs7, // 填充方式
	    iv,
	});
	return decrypted.toString(CryptoJS.enc.Utf8);
};
console.log(encryptAES('text'))
console.log(decryptAES('r1K8/zmvT/G2jGop1SwTLA=='))

// DES-encrypt
function encryptDES(text) {
    let key = CryptoJS.enc.Utf8.parse('01234567'); // 8字节密钥
    let iv = CryptoJS.enc.Utf8.parse('abcdef01'); // 8字节偏移量
    let encrypted = CryptoJS.DES.encrypt(text, key, { 
    	mode: CryptoJS.mode.CBC,
    	padding: CryptoJS.pad.Pkcs7,
    	iv
    });
    return encrypted.toString();
};
// DES-decrypt
function decryptDES(data) {
    let key = CryptoJS.enc.Utf8.parse('01234567'); // 8字节密钥
    let iv = CryptoJS.enc.Utf8.parse('abcdef01'); // 8字节偏移量
    let decrypt = CryptoJS.TripleDES.decrypt(data, key, { 
    	mode: CryptoJS.mode.CBC,
    	padding: CryptoJS.pad.Pkcs7,
    	iv
    });
    return decrypt.toString(CryptoJS.enc.Utf8);
};
console.log(encryptDES('text'))
console.log(decryptDES('YfO67tNGja8='))

// 3DES-encrypt
function encrypt3des(text) {
	let key = CryptoJS.enc.Utf8.parse('0123456789abcdef01234567'); // 24字节密钥
	let iv = CryptoJS.enc.Utf8.parse('abcdef0123456789abcdef01'); // 24字节偏移量
	let encrypted = CryptoJS.TripleDES.encrypt(text, key, {
	    mode: CryptoJS.mode.CBC, // 加密模式
	    padding: CryptoJS.pad.Pkcs7, // 填充方式
	    iv,
	});
	return encrypted.toString();
};
// 3DES-decrypt
function decrypt3des(text) {
    let key = CryptoJS.enc.Utf8.parse('0123456789abcdef01234567'); // 24字节密钥
	let iv = CryptoJS.enc.Utf8.parse('abcdef0123456789abcdef01'); // 24字节偏移量
	let decrypted  = CryptoJS.TripleDES.decrypt(text, key, {
	    mode: CryptoJS.mode.CBC, // 加密模式
	    padding: CryptoJS.pad.Pkcs7, // 填充方式
	    iv,
	});
	return decrypted.toString(CryptoJS.enc.Utf8);
};
console.log(encrypt3des('text'))
console.log(decrypt3des('hhCS773ry1U='))

```
