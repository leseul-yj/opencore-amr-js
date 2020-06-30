# opencore
## 音频加解密总结
1. 初始直接将解密后的二进制文件转化成blob，建立url，更改audio的src，音频无法播放；
2. web不支持安卓的录音格式(amr格式的音频)，需要将amr格式的音频进行转码;
3. 项目中从后端获取的文件是加密后的二进制，不能直接转码，应该先解密在进行转码;
4. audioContext 不支持amr
```js
		var audioCtx = new(window.AudioContext || window.webkitAudioContext)();
				var source = audioCtx.createBufferSource();
				audioCtx.decodeAudioData(ArrayBufferUtils.fromArray(decryptArray), function(decodedData) {
					source.buffer = decodedData;
					source.connect(audioCtx.destination);
					source.start(0);
				});

   ```
## 视频解密总结
1. 最初使用mediaSource 但是会报错，说视频格式是非fragment，网络上的解决办法将视频转化格式，但是视频是从其他端传过的，转化格式不现实；
2. 将blob的type设置为 'video/webm; codecs=h264'；


