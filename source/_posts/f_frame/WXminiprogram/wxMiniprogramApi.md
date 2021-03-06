# 基础
wx.canIUse(string schema) => boolean
判断小程序的AP
wx.base64ToArrayBuffer
要转化成 ArrayBuffer 对象的 Base64 字符串
wx.arrayBufferToBase64(ArrayBuffer arrayBuffer)
将 ArrayBuffer 对象转成 Base64 字符串

# 系统
系统信息
wx.getSystemInfoSync
获取系统信息(同步版)
wx.getSystemInfoAsync
获取系统信息
wx.getSystemInfo
获取系统信息

# 更新
wx.updateWeChatApp
wx.getUpdateManager
UpdateManager
UpdateManager.applyUpdate
UpdateManager.onCheckForUpdate
UpdateManager.onUpdateFailed
UpdateManager.onUpdateReady
小程序

# 生命周期
wx.getLaunchOptionsSync
wx.getEnterOptionsSync
应用级事件
wx.onUnhandledRejection
wx.onThemeChange
wx.onPageNotFound
wx.onError
wx.onAudioInterruptionEnd
wx.onAudioInterruptionBegin
wx.onAppShow
wx.onAppHide
wx.offUnhandledRejection
wx.offThemeChange
wx.offPageNotFound
wx.offError
wx.offAudioInterruptionEnd
wx.offAudioInterruptionBegin
wx.offAppShow
wx.offAppHide

# 调试
wx.setEnableDebug
wx.getRealtimeLogManager
wx.getLogManager
console
console.debug
console.error
console.group
console.groupEnd
console.info
console.log
console.warn
LogManager
LogManager.debug
LogManager.info
LogManager.log
LogManager.warn
RealtimeLogManager
RealtimeLogManager.addFilterMsg
RealtimeLogManager.error
RealtimeLogManager.in
RealtimeLogManager.info
RealtimeLogManager.setFilterMsg
RealtimeLogManager.tag
RealtimeLogManager.warn
RealtimeTagLogManager
RealtimeTagLogManager.error
RealtimeTagLogManager.info
RealtimeTagLogManager.setFilterMsg
RealtimeTagLogManager.warn
RealtimeTagLogManager.addFilterMsg

# 定时器
clearInterval
clearTimeout
setInterval
setTimeout

# 环境变量
env


# 路由
wx.switchTab
wx.reLaunch
wx.redirectTo
wx.navigateTo
wx.navigateBack
EventChannel
EventChannel.emit
EventChannel.off
EventChannel.on
EventChannel.once

# 界面
交互
wx.showToast({title[, icon, image, duration, mask, success, fail, complete]})
显示消息提示框
object: {title, icon, image, duration, mask, success, fail, complete}
wx.showModal([{title, content, showCancel, cancelText, cancelColor, confirmText, confirmColor, success, fail, complete}])
iconLegalValue: ['succes', 'error', 'loading', 'none']
显示模态对话框 
wx.showLoading({title[, mask, success, fail, complete]})
显示 loading 提示框
wx.showActionSheet({itemList[, alerText,  itemColor, success, fail, complete]})
successCallBackArgumentsValue: {tapIndex}
显示操作菜单
wx.hideToast
wx.hideLoading()
关闭 loading 提示框
wx.enableAlertBeforeUnload({message[, success, fail, complete]})
开启小程序页面返回询问对话框
wx.disableAlertBeforeUnload

# 导航栏
wx.showNavigationBarLoading
wx.setNavigationBarTitle
wx.setNavigationBarColor
wx.hideNavigationBarLoading
wx.hideHomeButton

# 背景
wx.setBackgroundTextStyle
wx.setBackgroundColor
Tab Bar
wx.showTabBarRedDot
wx.showTabBar
wx.setTabBarStyle
wx.setTabBarItem
wx.setTabBarBadge
wx.removeTabBarBadge
wx.hideTabBarRedDot
wx.hideTabBar

# 字体
wx.loadFontFace

# 下拉刷新
wx.stopPullDownRefresh
wx.startPullDownRefresh

# 滚动
wx.pageScrollTo
ScrollViewContext
ScrollViewContext.scrollIntoView
ScrollViewContext.scrollTo

# 动画
wx.createAnimation
Animation
Animation.matrix
Animation.matrix3d
Animation.opacity
Animation.right
Animation.rotate
Animation.rotate3d
Animation.rotateX
Animation.rotateY
Animation.rotateZ
Animation.scale
Animation.scale3d
Animation.scaleX
Animation.scaleY
Animation.scaleZ
Animation.skew
Animation.skewX
Animation.skewY
Animation.step
Animation.top
Animation.translate
Animation.translate3d
Animation.translateX
Animation.translateY
Animation.translateZ
Animation.width
Animation.bottom
Animation.export
Animation.backgroundColor
Animation.height
Animation.left

# 置顶
wx.setTopBarText

# 自定义组件
wx.nextTick

# 菜单
wx.getMenuButtonBoundingClientRect

# 窗口
wx.setWindowSize
wx.onWindowResize
wx.offWindowResize

# 键盘
wx.onKeyboardHeightChange
wx.offKeyboardHeightChange
wx.hideKeyboard
wx.getSelectedTextRange


# 网络

wx.request(Object object)
发起请求
object: {url,data,header,method,dataType,success,fail,complete}
RequestTask
RequestTask.abort
RequestTask.offHeadersReceived
RequestTask.onHeadersReceived

# 下载
wx.downloadFile
DownloadTask
DownloadTask.abort
DownloadTask.offHeadersReceived
DownloadTask.offProgressUpdate
DownloadTask.onHeadersReceived
DownloadTask.onProgressUpdate
# 上传

wx.uploadFile
UploadTask
UploadTask.abort
UploadTask.offHeadersReceived
UploadTask.offProgressUpdate
UploadTask.onHeadersReceived
UploadTask.onProgressUpdate
WebSocket
wx.sendSocketMessage
wx.onSocketOpen
wx.onSocketMessage
wx.onSocketError
wx.onSocketClose
wx.connectSocket
wx.closeSocket
SocketTask
SocketTask.close
SocketTask.onClose
SocketTask.onError
SocketTask.onMessage
SocketTask.onOpen
SocketTask.send
mDNS
wx.stopLocalServiceDiscovery
wx.startLocalServiceDiscovery
wx.onLocalServiceResolveFail
wx.onLocalServiceLost
wx.onLocalServiceFound
wx.onLocalServiceDiscoveryStop
wx.offLocalServiceResolveFail
wx.offLocalServiceLost
wx.offLocalServiceFound
wx.offLocalServiceDiscoveryStop
# UDP 通信

wx.createUDPSocket
UDPSocket
UDPSocket.bind
UDPSocket.close
UDPSocket.connect
UDPSocket.offClose
UDPSocket.offError
UDPSocket.offListening
UDPSocket.offMessage
UDPSocket.onClose
UDPSocket.onError
UDPSocket.onListening
UDPSocket.onMessage
UDPSocket.send
UDPSocket.write

# 数据缓存
wx.setStorageSync({key, data, success, fail, complete})
设置同步数据缓存
wx.setStorage({key, data[, success[, fail[, complete]]]})
设置数据缓存
wx.removeStorageSync
wx.removeStorage
wx.getStorageSync(string key)
同步版获取缓存
wx.getStorageInfoSync
wx.getStorageInfo
wx.getStorage({key, success, fail, complete})
获取缓存
object: {key, success, fail, complete}
wx.clearStorageSync
wx.clearStorage
周期性更新
wx.setBackgroundFetchToken
wx.onBackgroundFetchData
wx.getBackgroundFetchToken
wx.getBackgroundFetchData
# 媒体

地图
wx.createMapContext
MapContext
MapContext.addCustomLayer
MapContext.addGroundOverlay
MapContext.addMarkers
MapContext.fromScreenLocation
MapContext.getCenterLocation
MapContext.getRegion
MapContext.getRotate
MapContext.getScale
MapContext.getSkew
MapContext.includePoints
MapContext.initMarkerCluster
MapContext.moveAlong
MapContext.moveToLocation
MapContext.on
MapContext.openMapApp
MapContext.removeCustomLayer
MapContext.removeGroundOverlay
MapContext.removeMarkers
MapContext.setCenterOffset
MapContext.setLocMarkerIcon
MapContext.toScreenLocation
MapContext.translateMarker
MapContext.updateGroundOverlay
# 图片

wx.saveImageToPhotosAlbum
wx.previewMedia
wx.previewImage
wx.getImageInfo
wx.compressImage
wx.chooseMessageFile
wx.chooseImage
# 视频

wx.saveVideoToPhotosAlbum
wx.openVideoEditor
wx.getVideoInfo
wx.createVideoContext
wx.compressVideo
wx.chooseVideo
wx.chooseMedia
VideoContext
VideoContext.exitBackgroundPlayback
VideoContext.exitFullScreen
VideoContext.exitPictureInPicture
VideoContext.hideStatusBar
VideoContext.pause
VideoContext.play
VideoContext.playbackRate
VideoContext.requestBackgroundPlayback
VideoContext.requestFullScreen
VideoContext.seek
VideoContext.sendDanmu
VideoContext.showStatusBar
VideoContext.stop
# 音频

wx.stopVoice
wx.setInnerAudioOption
wx.playVoice
wx.pauseVoice
wx.getAvailableAudioSources
wx.createMediaAudioPlayer
wx.createInnerAudioContext
wx.createAudioContext
InnerAudioContext
InnerAudioContext.destroy
InnerAudioContext.offCanplay
InnerAudioContext.offEnded
InnerAudioContext.offError
InnerAudioContext.offPause
InnerAudioContext.offPlay
InnerAudioContext.offSeeked
InnerAudioContext.offSeeking
InnerAudioContext.offStop
InnerAudioContext.offTimeUpdate
InnerAudioContext.offWaiting
InnerAudioContext.onCanplay
InnerAudioContext.onEnded
InnerAudioContext.onError
InnerAudioContext.onPause
InnerAudioContext.onPlay
InnerAudioContext.onSeeked
InnerAudioContext.onSeeking
InnerAudioContext.onStop
InnerAudioContext.onTimeUpdate
InnerAudioContext.onWaiting
InnerAudioContext.pause
InnerAudioContext.play
InnerAudioContext.seek
InnerAudioContext.stop
MediaAudioPlayer
MediaAudioPlayer.addAudioSource
MediaAudioPlayer.destroy
MediaAudioPlayer.removeAudioSource
MediaAudioPlayer.start
MediaAudioPlayer.stop
AudioContext
AudioContext.pause
AudioContext.play
AudioContext.seek
AudioContext.setSrc
# 背景音频

wx.stopBackgroundAudio
wx.seekBackgroundAudio
wx.playBackgroundAudio
wx.pauseBackgroundAudio
wx.onBackgroundAudioStop
wx.onBackgroundAudioPlay
wx.onBackgroundAudioPause
wx.getBackgroundAudioPlayerState
wx.getBackgroundAudioManager
BackgroundAudioManager
BackgroundAudioManager.onCanplay
BackgroundAudioManager.onEnded
BackgroundAudioManager.onError
BackgroundAudioManager.onNext
BackgroundAudioManager.onPause
BackgroundAudioManager.onPlay
BackgroundAudioManager.onPrev
BackgroundAudioManager.onSeeked
BackgroundAudioManager.onSeeking
BackgroundAudioManager.onStop
BackgroundAudioManager.onTimeUpdate
BackgroundAudioManager.onWaiting
BackgroundAudioManager.pause
BackgroundAudioManager.play
BackgroundAudioManager.seek
BackgroundAudioManager.stop
# 实时音视频

wx.createLivePusherContext
wx.createLivePlayerContext
LivePlayerContext
LivePlayerContext.exitFullScreen
LivePlayerContext.exitPictureInPicture
LivePlayerContext.mute
LivePlayerContext.pause
LivePlayerContext.play
LivePlayerContext.requestFullScreen
LivePlayerContext.requestPictureInPicture
LivePlayerContext.resume
LivePlayerContext.snapshot
LivePlayerContext.stop
LivePusherContext
LivePusherContext.pause
LivePusherContext.pauseBGM
LivePusherContext.playBGM
LivePusherContext.resume
LivePusherContext.resumeBGM
LivePusherContext.sendMessage
LivePusherContext.setBGMVolume
LivePusherContext.setMICVolume
LivePusherContext.snapshot
LivePusherContext.start
LivePusherContext.startPreview
LivePusherContext.stop
LivePusherContext.stopBGM
LivePusherContext.stopPreview
LivePusherContext.switchCamera
LivePusherContext.toggleTorch
# 录音

wx.stopRecord
wx.startRecord
wx.getRecorderManager
RecorderManager
RecorderManager.onError
RecorderManager.onFrameRecorded
RecorderManager.onInterruptionBegin
RecorderManager.onInterruptionEnd
RecorderManager.onPause
RecorderManager.onResume
RecorderManager.onStart
RecorderManager.onStop
RecorderManager.pause
RecorderManager.resume
RecorderManager.start
RecorderManager.stop
# 相机

wx.createCameraContext
CameraContext
CameraContext.setZoom
CameraContext.startRecord
CameraContext.stopRecord
CameraContext.takePhoto
CameraContext.onCameraFrame
CameraFrameListener
CameraFrameListener.start
CameraFrameListener.stop
# 富文本

EditorContext
EditorContext.blur
EditorContext.clear
EditorContext.format
EditorContext.getContents
EditorContext.getSelectionText
EditorContext.insertDivider
EditorContext.insertImage
EditorContext.insertText
EditorContext.redo
EditorContext.removeFormat
EditorContext.scrollIntoView
EditorContext.setContents
EditorContext.undo
# 音视频合成

wx.createMediaContainer
MediaContainer
MediaContainer.addTrack
MediaContainer.destroy
MediaContainer.export
MediaContainer.extractDataSource
MediaContainer.removeTrack
MediaTrack
# 实时语音

wx.updateVoIPChatMuteConfig
wx.subscribeVoIPVideoMembers
wx.onVoIPVideoMembersChanged
wx.onVoIPChatSpeakersChanged
wx.onVoIPChatMembersChanged
wx.onVoIPChatInterrupted
wx.offVoIPVideoMembersChanged
wx.offVoIPChatMembersChanged
wx.offVoIPChatInterrupted
wx.joinVoIPChat
wx.exitVoIPChat
# 画面录制器

wx.createMediaRecorder
MediaRecorder
MediaRecorder.destroy
MediaRecorder.off
MediaRecorder.on
MediaRecorder.pause
MediaRecorder.requestFrame
MediaRecorder.resume
MediaRecorder.start
MediaRecorder.stop
# 视频解码器

wx.createVideoDecoder
VideoDecoder
VideoDecoder.getFrameData
VideoDecoder.off
VideoDecoder.on
VideoDecoder.remove
VideoDecoder.seek
VideoDecoder.start
VideoDecoder.stop
# 位置

wx.stopLocationUpdate
wx.startLocationUpdateBackground
wx.startLocationUpdate
wx.openLocation
wx.onLocationChange
wx.offLocationChange
wx.getLocation
wx.choosePoi
wx.chooseLocation
# 转发

wx.updateShareMenu
wx.showShareMenu
wx.showShareImageMenu
wx.shareVideoMessage
wx.shareFileMessage
wx.onCopyUrl
wx.offCopyUrl
wx.hideShareMenu
wx.getShareInfo
wx.authPrivateMessage
# 画布

wx.createOffscreenCanvas
wx.createCanvasContext
wx.canvasToTempFilePath
wx.canvasPutImageData
wx.canvasGetImageData
Canvas
Canvas.cancelAnimationFrame
Canvas.createImage
Canvas.createImageData
Canvas.createPath2D
Canvas.getContext
Canvas.requestAnimationFrame
Canvas.toDataURL
CanvasContext
CanvasContext.arc
CanvasContext.arcTo
CanvasContext.beginPath
CanvasContext.bezierCurveTo
CanvasContext.clearRect
CanvasContext.clip
CanvasContext.closePath
CanvasContext.createCircularGradient
CanvasContext.createLinearGradient
CanvasContext.createPattern
CanvasContext.draw
CanvasContext.drawImage
CanvasContext.fill
CanvasContext.fillRect
CanvasContext.fillText
CanvasContext.lineTo
CanvasContext.measureText
CanvasContext.moveTo
CanvasContext.quadraticCurveTo
CanvasContext.rect
CanvasContext.restore
CanvasContext.rotate
CanvasContext.save
CanvasContext.scale
CanvasContext.setFillStyle
CanvasContext.setFontSize
CanvasContext.setGlobalAlpha
CanvasContext.setLineCap
CanvasContext.setLineDash
CanvasContext.setLineJoin
CanvasContext.setLineWidth
CanvasContext.setMiterLimit
CanvasContext.setShadow
CanvasContext.setStrokeStyle
CanvasContext.setTextAlign
CanvasContext.setTextBaseline
CanvasContext.setTransform
CanvasContext.stroke
CanvasContext.strokeRect
CanvasContext.strokeText
CanvasContext.transform
CanvasContext.translate
CanvasGradient
CanvasGradient.addColorStop
Color
Image
ImageData
OffscreenCanvas
OffscreenCanvas.createImage
OffscreenCanvas.getContext
Path2D
RenderingContext
# 文件

wx.saveFileToDisk
wx.saveFile
wx.removeSavedFile
wx.openDocument
wx.getSavedFileList
wx.getSavedFileInfo
wx.getFileSystemManager
wx.getFileInfo
FileSystemManager
FileSystemManager.access
FileSystemManager.accessSync
FileSystemManager.appendFile
FileSystemManager.appendFileSync
FileSystemManager.close
FileSystemManager.closeSync
FileSystemManager.copyFile
FileSystemManager.copyFileSync
FileSystemManager.fstat
FileSystemManager.fstatSync
FileSystemManager.ftruncate
FileSystemManager.ftruncateSync
FileSystemManager.getFileInfo
FileSystemManager.getSavedFileList
FileSystemManager.mkdir
FileSystemManager.mkdirSync
FileSystemManager.open
FileSystemManager.openSync
FileSystemManager.read
FileSystemManager.readdir
FileSystemManager.readdirSync
FileSystemManager.readFile
FileSystemManager.readFileSync
FileSystemManager.readSync
FileSystemManager.removeSavedFile
FileSystemManager.rename
FileSystemManager.renameSync
FileSystemManager.rmdir
FileSystemManager.rmdirSync
FileSystemManager.saveFile
FileSystemManager.saveFileSync
FileSystemManager.stat
FileSystemManager.statSync
FileSystemManager.truncate
FileSystemManager.truncateSync
FileSystemManager.unlink
FileSystemManager.unlinkSync
FileSystemManager.unzip
FileSystemManager.write
FileSystemManager.writeFile
FileSystemManager.writeFileSync
FileSystemManager.writeSync
readResult
Stats
Stats.isDirectory
Stats.isFile
writeResult

# 开放接口

登录
wx.login({timeout, success, fail, complete}) 
success: res => {code}

wx.checkSession
小程序跳转
wx.navigateToMiniProgram
wx.navigateBackMiniProgram
帐号信息
wx.getAccountInfoSync
用户信息
wx.getUserProfile
wx.getUserInfo
UserInfo
数据上报
wx.reportMonitor
wx.reportEvent
wx.getExptInfoSync
数据分析
wx.reportAnalytics

# 支付
wx.requestPayment
wx.requestOrderPayment

# 授权
wx.authorizeForMiniProgram({scope, success, fail, complete})
scopeLegalValue: ['scope.userInfo', 'scope.userLocation', 'scope.userLocationBackground', 'scope.address', 'scope.invoiceTitle', 'scope.invoice', 'scope.werun', 'scope.record', 'scope.writePhotosAlbum', 'scope.camera' ]
获取授权
wx.authorize({scope, success, fail, complete})
scopeLegalValue: ['scope.userInfo', 'scope.userLocation', 'scope.userLocationBackground', 'scope.address', 'scope.invoiceTitle', 'scope.invoice', 'scope.werun', 'scope.record', 'scope.writePhotosAlbum', 'scope.camera' ]
提前向用户发起授权请求

设置
wx.openSetting({withSubscriptions, success, fail, complete})
调起客户端小程序设置界面，返回用户设置的操作结果
wx.getSetting({withSubscriptions, success, fail, complete})
获取用户的当前设置
AuthSetting
用户授权设置信息
SubscriptionsSetting
订阅消息设置

收货地址
wx.chooseAddress
卡券
wx.openCard
wx.addCard
发票
wx.chooseInvoiceTitle
wx.chooseInvoice
生物认证
wx.startSoterAuthentication
wx.checkIsSupportSoterAuthentication
wx.checkIsSoterEnrolledInDevice
微信运动
wx.shareToWeRun
wx.getWeRunData
性能
wx.reportPerformance
wx.getPerformance
EntryList
EntryList.getEntries
EntryList.getEntriesByName
EntryList.getEntriesByType
Performance
Performance.createObserver
Performance.getEntries
Performance.getEntriesByName
Performance.getEntriesByType
Performance.setBufferSize
PerformanceObserver
PerformanceObserver.disconnect
PerformanceObserver.observe
订阅消息
wx.requestSubscribeMessage
微信红包
wx.showRedPackage
群工具
wx.getGroupEnterInfo
设备
NFC
wx.stopHCE
wx.startHCE
wx.sendHCEMessage
wx.onHCEMessage
wx.offHCEMessage
wx.getNFCAdapter
wx.getHCEState
MifareClassic
MifareClassic.close
MifareClassic.connect
MifareClassic.getMaxTransceiveLength
MifareClassic.isConnected
MifareClassic.setTimeout
MifareClassic.transceive
IsoDep
IsoDep.close
IsoDep.connect
IsoDep.getHistoricalBytes
IsoDep.getMaxTransceiveLength
IsoDep.isConnected
IsoDep.setTimeout
IsoDep.transceive
MifareUltralight
MifareUltralight.close
MifareUltralight.connect
MifareUltralight.getMaxTransceiveLength
MifareUltralight.isConnected
MifareUltralight.setTimeout
MifareUltralight.transceive
Ndef
Ndef.close
Ndef.connect
Ndef.isConnected
Ndef.offNdefMessage
Ndef.onNdefMessage
Ndef.setTimeout
Ndef.writeNdefMessage
NfcA
NfcA.close
NfcA.connect
NfcA.getAtqa
NfcA.getMaxTransceiveLength
NfcA.getSak
NfcA.isConnected
NfcA.setTimeout
NfcA.transceive
NFCAdapter
NFCAdapter.getIsoDep
NFCAdapter.getMifareClassic
NFCAdapter.getMifareUltralight
NFCAdapter.getNdef
NFCAdapter.getNfcA
NFCAdapter.getNfcB
NFCAdapter.getNfcF
NFCAdapter.getNfcV
NFCAdapter.offDiscovered
NFCAdapter.onDiscovered
NFCAdapter.startDiscovery
NFCAdapter.stopDiscovery
NfcB
NfcB.close
NfcB.connect
NfcB.getMaxTransceiveLength
NfcB.isConnected
NfcB.setTimeout
NfcB.transceive
NfcF
NfcF.close
NfcF.connect
NfcF.getMaxTransceiveLength
NfcF.isConnected
NfcF.setTimeout
NfcF.transceive
NfcV
NfcV.close
NfcV.connect
NfcV.getMaxTransceiveLength
NfcV.isConnected
NfcV.setTimeout
NfcV.transceive
外围设备
wx.onBLEPeripheralConnectionStateChanged
wx.offBLEPeripheralConnectionStateChanged
wx.createBLEPeripheralServer
BLEPeripheralServer
BLEPeripheralServer.addService
BLEPeripheralServer.close
BLEPeripheralServer.offCharacteristicReadRequest
BLEPeripheralServer.offCharacteristicSubscribed
BLEPeripheralServer.offCharacteristicUnsubscribed
BLEPeripheralServer.offCharacteristicWriteRequest
BLEPeripheralServer.onCharacteristicReadRequest
BLEPeripheralServer.onCharacteristicSubscribed
BLEPeripheralServer.onCharacteristicUnsubscribed
BLEPeripheralServer.onCharacteristicWriteRequest
BLEPeripheralServer.removeService
BLEPeripheralServer.startAdvertising
BLEPeripheralServer.stopAdvertising
BLEPeripheralServer.writeCharacteristicValue
iBeacon
wx.stopBeaconDiscovery
wx.startBeaconDiscovery
wx.onBeaconUpdate
wx.onBeaconServiceChange
wx.offBeaconUpdate
wx.offBeaconServiceChange
wx.getBeacons
IBeaconInfo
Wi-Fi
wx.stopWifi
wx.startWifi
wx.setWifiList
wx.onWifiConnected
wx.onGetWifiList
wx.offWifiConnected
wx.offGetWifiList
wx.getWifiList
wx.getConnectedWifi
wx.connectWifi
WifiInfo
低功耗蓝牙
wx.setBLEMTU
wx.readBLECharacteristicValue
wx.onBLEConnectionStateChange
wx.onBLECharacteristicValueChange
wx.offBLEConnectionStateChange
wx.offBLECharacteristicValueChange
wx.notifyBLECharacteristicValueChange
wx.makeBluetoothPair
wx.getBLEDeviceServices
wx.getBLEDeviceRSSI
wx.getBLEDeviceCharacteristics
wx.createBLEConnection
wx.closeBLEConnection
wx.writeBLECharacteristicValue
日历
wx.addPhoneRepeatCalendar
wx.addPhoneCalendar
联系人
wx.searchContacts
wx.chooseContact
wx.addPhoneContact
无障碍
wx.checkIsOpenAccessibility
蓝牙
wx.stopBluetoothDevicesDiscovery
wx.startBluetoothDevicesDiscovery
wx.openBluetoothAdapter
wx.onBluetoothDeviceFound
wx.onBluetoothAdapterStateChange
wx.offBluetoothDeviceFound
wx.offBluetoothAdapterStateChange
wx.getConnectedBluetoothDevices
wx.getBluetoothDevices
wx.getBluetoothAdapterState
wx.closeBluetoothAdapter
电量
wx.getBatteryInfoSync
wx.getBatteryInfo
剪贴板
wx.setClipboardData
wx.getClipboardData
网络
wx.onNetworkStatusChange
wx.offNetworkStatusChange
wx.getNetworkType
加密
wx.getRandomValues
屏幕
wx.setScreenBrightness
wx.setKeepScreenOn
wx.onUserCaptureScreen
wx.offUserCaptureScreen
wx.getScreenBrightness
电话
wx.makePhoneCall
加速计
wx.stopAccelerometer
wx.startAccelerometer
wx.onAccelerometerChange
wx.offAccelerometerChange
罗盘
wx.stopCompass
wx.startCompass
wx.onCompassChange
wx.offCompassChange
设备方向
wx.stopDeviceMotionListening
wx.startDeviceMotionListening
wx.onDeviceMotionChange
wx.offDeviceMotionChange
陀螺仪
wx.stopGyroscope
wx.startGyroscope
wx.onGyroscopeChange
wx.offGyroscopeChange
性能
wx.onMemoryWarning
wx.offMemoryWarning
扫码
wx.scanCode
振动
wx.vibrateShort
wx.vibrateLong
Worker
wx.createWorker
Worker
Worker.onMessage
Worker.onProcessKilled
Worker.postMessage
Worker.terminate
第三方平台
wx.getExtConfigSync
wx.getExtConfig
WXML
wx.createSelectorQuery
wx.createIntersectionObserver
IntersectionObserver
IntersectionObserver.disconnect
IntersectionObserver.observe
IntersectionObserver.relativeTo
IntersectionObserver.relativeToViewport
MediaQueryObserver
MediaQueryObserver.disconnect
MediaQueryObserver.observe
NodesRef
NodesRef.boundingClientRect
NodesRef.context
NodesRef.fields
NodesRef.node
NodesRef.scrollOffset
SelectorQuery
SelectorQuery.exec
SelectorQuery.in
SelectorQuery.select
SelectorQuery.selectAll
SelectorQuery.selectViewport
广告
wx.createRewardedVideoAd
RewardedVideoAd
RewardedVideoAd.destroy
RewardedVideoAd.load
RewardedVideoAd.offClose
RewardedVideoAd.offError
RewardedVideoAd.offLoad
RewardedVideoAd.onClose
RewardedVideoAd.onError
RewardedVideoAd.onLoad
RewardedVideoAd.show
wx.addVideoToFavorites
wx.addFileToFavorites
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 