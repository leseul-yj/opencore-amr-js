# opencore
## 音频加解密总结
1. web不支持安卓的录音格式(amr格式的音频)，需要将amr格式的音频进行转码;
2. 项目中从后端获取的文件是加密后的二进制，不能直接转码，应该先解密在进行转码;


