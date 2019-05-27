> #### 什么是编解码器

编码器的作用是读取特定的容器格式, 并对其中的音频与视频轨道进行解码, 然后实现播放.音频和视频原始数据比较大, 我们往往

通过编码器对原始音频和视频文件进行有损压缩, 这样就便于在互联网上进行传输或播放。

> #### 常用的视频编解码器

| H\_246 | H.264是MPEG-4标准所定义的最新格式, 同时也是技术含量最高、代表最新技术水平的视频编码格式之一,有的也称\(AVC\) , 目前是主流。 |
| :---: | :--- |
| VP8 | Google公司的产品 。VP8是一个免版权费用可自由使用的技术, 任何使用都不受版权限制, 使用的比较少 |
| Ogg Theora | OggTheora是 xiph.Org第一个公开发布的视频编解码器, 在 Ogg项目和 Ogg 流媒体服务器中使用 |

#### ![](/assets/kt3.png)

> #### 常用的音频编解码器

| AAC | 高级音频编码。相对于mp3, AAc格式的音质更佳,文件更小。 苹果、 诺基亚等公司的设备支持AAC格式 |
| :---: | :--- |
| MP3 | MP3是一种音频压缩技术, 其全称是动态影像专家压缩标准音频层面3,主要是在美国和日本, 不包括欧盟国家, 如微软更倾向于使用 MP3格式 |
| Ogg Vorbis | Ogg是指一种文件格式, 开源且免使用费, 就是为了与需要专利使用费的 M P3和AAc一争高下 |

![](/assets/微信图片_20190526184709.jpg)

> #### 代码定义:

* [x] **播放音频**

```HTML
<audio controls="controls">
  <source src="kk.mp4" type="audio/ogg"/>
  <source src="kk.mp4" type="audio/mpeg"/>
  您的浏览器不支持audio元素
</audio>
```

* [x] **播放视频**

```HTML
<video src="kk.mp4" controls="controls">
  您的浏览器不支持audio元素
</video>
```

> #### 音频视频的相关属性

| src | 用于指定媒体资源的 URL地址 |
| :---: | :--- |
| autoplay | 该属性可以实现页面加载音频后一旦就绪即开始自动播放 |
| buffered | 用于返回一个TimeRanges对象, 确认浏览器已经缓存媒体文件 |
| controls | 可以为媒体文件提供用于播放的控制条,包含播放、暂停、定位、时间显示、音量控制、全房切换等常用控件 |
| currentSrc | 用于返回媒体数据的URL地址,如未指定地址,则返回一个空串 |
| ourrentTime | 用于获取或设置当前的播放位置,返回值为时间,单位为秒 |
| defaultPlaybackRate | 设置或返回音频/视频的默认播放速度 |
| loop | 设置或返回音频/视频是否应该在结束时重新播放 |
| duration | 用于获取当前媒体的持续时间 |
| muted | 设置或返回音频/视频是否应该被持音 \(关闭声音\) |
| networkState | 返回音频/视频的当前网络状态 |
| paused | 检查视频是否己暂停 |
| playbackRate | 设置返回音频/视频的当前播放速度。 |
| played | played属性返回 TimeRanges对象。TimeRanges 对象表示用户已经播放或看到的音频/视频范围 |
| preload | 设置或返回是否在页面加载后立即加载音频/视频 |
| readyState | 返回音频/视频的当前就绪状态 |
| seekable | 返回 TimeRanges 对象。表明可以对当前媒体资源进行请求 |
| volume | 属性设置或返回音频/视频的当前音量。必须是介于 0.0与1.0 之间的数字 |
| seeking | 返回用户目前是否正在音频/视频中请求数据 |

```js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>音频、视频相关方法</title>
</head>
<body>
<button onclick="getFirstBuffRange()" type="button">获得第一个缓冲范围</button>
<button onclick="getVid()" type="button">获得当前视频URL</button>
<br>
<button onclick="getCurTime()" type="button">获取视频当前播放时间</button>
<button onclick="setCurTime()" type="button">设置视频播放时间点</button>
<br>
<button onclick="getPlaySpeed()" type="button">获取视频默认播放速度</button>
<button onclick="setPlaySpeed()" type="button">设置视频播放速度</button>
<br>
<button onclick="getVidDur()" type="button">获取视频的播放长度</button>
<br>
<!--播放视频-->

<button onclick="enableLoop()" type="button">设置循环</button>
<button onclick="disableLoop()" type="button">取消循环</button>
<button onclick="checkLoop()" type="button">是否循环</button>
<br>
<button onclick="enableMute()" type="button">设置静音</button>
<button onclick="disableMute()" type="button">取消静音</button>
<button onclick="checkMute()" type="button">是否静音</button>
<br>
<button onclick="getNWState()" type="button">获取网络状态</button>
<button onclick="isVidPaused()" type="button">视频是否暂停</button>
<br>
<button onclick="getPlaySpeed()" type="button">获取视频速度</button>
<button onclick="setPlaySpeed()" type="button">减慢视频速度</button>
<br>
<button onclick="getFirstPlayedRange()" type="button">获得首段播放的范围</button>
<br>
<button onclick="enablePreload()" type="button">设置预加载</button>
<button onclick="disablePreload()" type="button">取消预加载</button>
<button onclick="checkPreload()" type="button">检查预加载状态</button>
<br>
<button onclick="getReadyState()" type="button">获取视频的就绪状态</button>
<br>
<button onclick="getFirstSeekableRange()" type="button">获得第一次可寻址范围</button>
<br>
<button onclick="getVolume()" type="button">获取当前音量</button>
<button onclick="setHalfVolume()" type="button">设置当前音量为0.2</button>
<button onclick="setFullVolume()" type="button">设置当前音量为1.0</button>
<br>
<video controls="controls" id="my_video" width="320" height="240" autoplay="autoplay">
  <source id="mp4_src" src="kk.mp4" type="video/mp4"/>
  <source id="ogg_src" src="kk.mp4" type="video/ogg"/>
  您的浏览器不支持video元素
</video>
<script>
  let myVideo = document.getElementById("my_video");

  //获得第一个缓冲范围
  function getFirstBuffRange() {
    alert("Start:" + myVideo.buffered.start(0) + "End:" + myVideo.buffered.end(0));
  }

  //获得当前视频URL
  function getVid() {
    alert(myVideo.currentSrc);
  }

  //获取视频当前播放时间
  function getCurTime() {
    alert(myVideo.currentTime);
  }

  // 设置视频播放时间点
  function setCurTime() {
    myVideo.currentTime = 5;
  }

  //获取视频的播放长度
  function getVidDur() {
    alert(myVideo.duration);
  }

  //是否循环
  function checkLoop() {
    alert(myVideo.loop);
  }

  //设置循环
  function enableLoop() {
    myVideo.loop = true;
    myVideo.load();
  }

  //取消循环
  function disableLoop() {
    myVideo.loop = false;
    myVideo.load();
  }

  //设置静音
  function enableMute() {
    myVideo.muted = true;
  }

  //取消静音
  function disableMute() {
    myVideo.muted = false;
  }

  //是否静音
  function checkMute() {
    alert(myVideo.muted);
  }

  //获取网络状态
  function getNWState() {
    alert(myVideo.networkState);
/*    表示音频/视频元素的当前网络状态：
    0 = NETWORK_EMPTY - 音频/视频尚未初始化
    1 = NETWORK_IDLE - 音频/视频是活动的且已选取资源，但并未使用网络
    2 = NETWORK_LOADING - 浏览器正在下载数据
    3 = NETWORK_NO_SOURCE - 未找到音频/视频来源 
*/
  }

  //视频是否暂停
  function isVidPaused() {
    alert(myVideo.paused);
  }

  //获取视频速度
  function getPlaySpeed() {
    alert(myVideo.playbackRate);
  }

  //减慢视频速度
  function setPlaySpeed() {
    myVideo.playbackRate = 0.5;
  }

  //获得视频中以秒计的首段已播放的范围
  function getFirstPlayedRange() {
    alert("Start:" + myVideo.played.start(0) + "End:" + myVideo.played.end(0));
  }

  //设置预加载(是否在页面加载后立即加载音频/视频)
  function enablePreload() {
    myVideo.preload = "auto";
  }

  //取消预加载
  function disablePreload() {
    myVideo.preload = "none";
  }

  //检查预加载状态
  function checkPreload() {
    alert(myVideo.preload);
  }

  //获取视频的就绪状态
  function getReadyState() {
    alert(myVideo.readyState);
  }

  //TimeRanges 对象表示音频/视频中用户可寻址的范围（可拖动缓存播放的位置）
  function getFirstSeekableRange() {
    alert("Start:" + myVideo.seekable.start(0) + "End:" + myVideo.seekable.end(0));
  }

  //获取当前音量
  function getVolume() {
    alert(myVideo.volume);
  }

  //设置当前音量为1.0
  function setFullVolume() {
    myVideo.volume = 1.0;
  }

  //设置当前音量为0.2
  function setHalfVolume() {
    myVideo.volume = 0.2;
  }
</script>
</body>
</html>

```

> #### 音频视频相关方法

| canPlayType\(\) | 检测测览器是否能播放指定的音频/视频类型 canPlayType\(\) 方法可返回下列值之一:“probably”  -浏览器最可能支持该音频/视频类型“maybe”     -  浏览器也许支持该音频/视频类型     “” -  \(空字符串\) 浏览器不支持该音频/视频类型 |
| :---: | :--- |
| load\(\) | 重新加载音频/视频元素. load\(\) 方法用于在更改来源或其他设置后对音频/视频元素进了更新 |
| pause\(\) | 停止\(暂停\)当前播放的音频或视频 |
| play\(\) | play\(\)方法开始播放当前的音频或视频。 所有主流浏览器都支持 play\(\) 方法 |

```js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>音频、视频相关方法</title>
  <script>
    let myVideo = null;

    //检测浏览器是否对视频资源支持
    function supportType(vidType, codeType) {
      let myVid = document.createElement("video");
      let isSupp = myVid.canPlayType(vidType + ';codecs="' + codeType + '"');
      if (isSupp === "") {
        isSupp = "No";
      }
      alert(isSupp);
    }

    //切换视频资源
    function changeSource() {
      document.getElementById("mp4_src").src = "kk1.mp4";
      document.getElementById("ogg_src").src = "kk1.mp4";
      document.getElementById("my_video").load();
    }


    //播放视频
    function playVid() {
      myVideo = document.getElementById("my_video");
      myVideo.play();
    }

    //暂停视频
    function pauseVid() {
      myVideo = document.getElementById("my_video");
      myVideo.pause();
    }
  </script>
</head>
<body>
<p>浏览器是否支持播放MP4视频</p>
<button onclick="supportType('video/mp4','avc1.42E01E,mp4a.40.2')" type="button">Test</button>
<p>浏览器是否支持播放ogg视频</p>
<button onclick="supportType('video/ogg','theora,vorbis')" type="button">Test2</button>
<br>
<button onclick="changeSource()" type="button">切换视频资源</button>
<br>
<button onclick="playVid()" type="button">播放视频</button>
<br>
<button onclick="pauseVid()" type="button">暂停视频</button>
<br>
<video controls="controls" id="my_video" width="320" height="240">
  <source id="mp4_src" src="kk.mp4" type="video/mp4"/>
  <source id="ogg_src" src="kk.mp4" type="video/ogg"/>
  您的浏览器不支持video元素
</video>
</body>
</html>
```

> #### 音频视频的相关事件

| pause | 在音频/视频暂停时触发 |
| :---: | :--- |
| play | 在音频/视频开始播放时触发 |
| playing | 在音频/视频因缓冲而暂停或停止后已就绪时触发 |
| ratechange | 在音频/视频播放速度发生改变时触发\(如用户切换到慢速或快速播放模式\) |
| seeked | 在用户己移动/跳成到音频/视频中的新位置时触发 |
| seeking | 在用户开始移动/跳跌到新的音频/视频播放位置时触发 |
| stalled | 在浏览器尝试获取媒体数据, 但数据不可用时触发 |
| suspend | 在浏览器刻意不加载媒体数据时触发 |
| timeupdate | 在音频/视频的播放位置发生改变时触发 |
| volumechange | 在音频/视频的音量发生改变时触发 |
| waiting | 在视频由于需要缓下一帧而停止时触发 |
| canplay | 当浏览器能够开始播放指定的音频/视频时,会发生 canplay事件 |
| canplaythrough | 当浏览器预计能够在不停下来进行缓冲的情况下持续播放指定的音频/视频时,会发生 oanpIaythrough事件 |
| durationchange | 当指定音频/视频的时长数据发生变化时 |
| loadeddata | 当当前帧的数据已加载, 但没有足够的数据来播放指定音频/视频的下一帧时 |
| loadedmetadata | 当指定的音频/视频的元数据已加载时,会发生此事件。音频/ 视频的元数据包括:时长、尺寸\(仅视频\)以及文本轨道 |
| loadstart | 当浏览器开始寻找指定的音频/视频时 |
| progress | 当浏览器正在下载指定的音频/视频 |
| abort | 在音频/视频\(audio/video\)终止加载时触发 |
| ended | 在音频/视频\(audio/video\)播放完成后触发 |
| error | 在音频/视频\(audio/video\)加载发生错误时触发 |



