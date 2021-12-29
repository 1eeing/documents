## CHANGELOG

### 2021-12-29 @ v2.3.0
#### 新增特性
* 会中支持主持人视频会控功能
* 支持入会时设置使用通话、音乐等音频模式：创建对应`NEAudioProfile`对象并赋值给`NEMeetingOptions.audioProfile`字段
* 支持通过设置 `NEMeetingOptions.showMemberTag` 字段控制成员标签(`NEMeetingParams.tag`)是否显示在参会者列表中
* 创建/预约会议增加透传的扩展字段：
  * 通过`NEStartMeetingParams.extraData`与`NEMeetingItem.setExtraData`设置扩展字段
  * 通过获取会议信息后读取`NEMeetingInfo#extraData`可获取设置的扩展字段
* 创建/预约会议增加音视频控制字段，可设置成员入会时音视频的开关状态：
  * 创建即刻会议时设置：`NEStartMeetingParams.controls`
  * 预约会议时设置：`NEMeetingItemSetting.controls`

#### 接口废弃
* 废弃 `NEMeetingOptions.audioAINSEnabled`，请使用 `NEMeetingOptions.audioProfile` 来开启/关闭智能降噪
* 废弃 `NEMeetingItemSetting.isAttendeeAudioOff`，请使用 `NEMeetingItemSetting.controls` 来控制成员入会时的音频状态


### 2021-12-09 @ v2.2.0
#### 新增特性
* 支持音视频私有化部署

#### 问题修复
* 修复画廊模式小圆点显示被底部工具栏覆盖的问题
* 修复其他已知问题

### 2021-9-28 @ v2.0.6
#### 新增特性
* 新增会议语音智能降噪，入会前可打开/关闭，默认打开：`NEMeetingOptions.audioAINSEnabled`
* 新增静音时说话检测
* 优化音量大小UI展示

### v2.0.0 (2021-8-16)

####  新增特性

* 创建即刻会议时可设置会议密码：`NEMeetingParams.password`
* 创建/加入会议时可设置连接超时时间，超时会自动离开：`NEMeetingOptions.joinTimeout`
* 新增离开会议接口：`NEMeetingService.leaveCurrentMeeting`
* 支持更细粒度的会议退出码，详情请查看 `NEMeetingCode`


####  功能更新

* 创建会议时，如果设置了`NEMeetingOptions.noChat`为`true`，将不再会创建聊天室

### v1.10.0 (2021-7-9)

####  新增特性

* 创建和加入会议可设置成员标签，对应字段为：`NEMeetingParams.tag`
* 会议中的成员信息类可获取到入会时设置的成员标签，对应字段为：`NEInMeetingUserInfo.tag`
* 预约会议和创建会议时，可配置允许入会的成员账号列表以及数量：
  - 创建会议时使用`NEStartMeetingParams.scene`字段配置
  - 预约会议时使用`NEMeetingItemSetting.scene`字段配置

###  v1.9.0 (2021-5-30)

####  新增特性

* SDK初始化时支持设置SDK日志路径与日志级别
  - 通过`NEMeetingSDKConfig.loggerConfig`字段设置
* 新增参会者用户信息类`NEInMeetingUserInfo`，包含用户Id与用户昵称
* 会议信息`NEMeetingInfo`新增以下字段：
  - 新增`NEMeetingInfo.userList`字段，可获取当前时刻会议中的参会者信息列表
  - 新增`NEMeetingInfo.hostUserId`字段，代表当前时刻会议的主持人用户Id

####  问题修复

* 修复屏幕共享分辨率选择不正确导致的画面模糊问题

####  Deprecated

* 废弃`NEMeetingSDKConfig.enableDebugLog`，使用`NEMeetingSDKConfig.loggerConfig`代替
* 废弃`NEMeetingSDKConfig.logSize`，使用`NEMeetingSDKConfig.loggerConfig`代替

### v1.8.1 (2021-5-01)

####  新增特性

* 支持屏幕共享辅流
* 支持会议云端录制功能开关
  - 新增`NEMeetingItemSetting.cloudRecordOn`预约会议选项配置“云端录制”是否开启
  - 新增`NEStartMeetingOptions.noCloudRecord`创建会议选项配置“云端录制”是否开启
* 会议信息新增sipId字段
  - 新增`NEMeetingInfo.sipId`字段
  - 新增`NEHistoryMeetingItem.sipId`字段

### v1.7.2 (2021-4-30)

####  新增特性

* 支持预约会议设置直播安全模式 

- 新增`NEMeetingItemLive.NEMeetingLiveAuthLevel`选项配置“直播安全模式”

### v1.7.0 (2021-3-18)

####  新增特性

* 支持会中改名，新增`NEMeetingOptions.noRename`选项配置该功能是否开启，默认为开启
* 支持查询历史参会记录信息，通过`NESettingsService.getHistoryMeetingItem`接口可返回最近一次的参会信息
* 新增会中白板功能
  - 新增白板菜单项，控制开启白板共享和结束白板共享
  - 新增`NEStartMeetingOptions.noWhiteBoard`选项配置白板功能是否开启，默认开启
* 新增`NEStartMeetingOptions.defaultWindowMode`选项配置“会议视图模式”，支持普通和白板模式
* 新增会中主持人可结束其他端共享（屏幕/白板）
* 优化会中邀请页面，时间显示格式为24小时制
* 支持会中聊天室文本消息长按复制


### v1.6.0 (2021-2-05)

####  新增特性

* 增加会议内白板菜单自定义

- 新增`NEMeetingSDK.getInstance().getMeetingService().NEStartMeetingOptions defaultWindowMode`
  配置“默认会议视图模式”
- 新增`NEMeetingSDK.getInstance().getMeetingService().NEStartMeetingOptions noWhiteBoard`
  配置“默认会议是否显示白板入口”
- 新增会中白板功能
- 新增会中主持人结束其他端共享（屏幕/白板）
- 优化会中邀请页面，时间显示格式为24小时制

### v1.5.2 (2021-1-15)

####  新增特性

* 支持自定义音频流
  - 订阅会议内某一音视频流：`NEMeetingService.subscribeRemoteAudioStream`
  - 批量订阅会议内某一音视频流：`NEMeetingService.subscribeRemoteAudioStreams`
  - 订阅会议内全部音视频流：`NEMeetingService.subscribeAllRemoteAudioStreams`

* 遥控器支持会议内菜单自定义
  - 新增单状态菜单项：`NESingleStateMenuItem`
  - 新增可切换状态的双状态菜单项：`NECheckableMenuItem`
  - 新增菜单项状态迁移控制器：`NEMenuStateController`
  - 新增SDK预置菜单Id与菜单项定义: `NEMenuIds`, `NEMenuItems`
  - [Android]新增菜单列表构建帮助类：`NEMenuItemListBuilder`
  - 配置工具栏菜单列表：`NEMeetingOptions.fullToolbarMenuItems`
  - 配置更多展开菜单列表：`NEMeetingOptions.fullMoreMenuItems`

#### v1.5.1 (2020-12-25)

####  问题修复

* 修复IM复用时登录状态错误

#### v1.5.0 (2020-12-21)

####  新增特性

* 支持会议内菜单自定义
  - 新增单状态菜单项：`NESingleStateMenuItem`
  - 新增可切换状态的双状态菜单项：`NECheckableMenuItem`
  - 新增菜单项状态迁移控制器：`NEMenuStateController`
  - 新增SDK预置菜单Id与菜单项定义: `NEMenuIds`, `NEMenuItems`
  - 新增菜单列表构建帮助类：`NEMenuItemListBuilder`
  - 配置工具栏菜单列表：`NEMeetingOptions.fullToolbarMenuItems`
  - 配置更多展开菜单列表：`NEMeetingOptions.fullMoreMenuItems`
* 新增直播功能
  - 直播开关状态查询：`NESettingsService.isMeetingLiveEnabled();`
* 设置服务新增美颜接口
  - 查询美颜状态开启状态：`NESettingsService.isBeautyFaceEnabled()`
  - 打开美颜预览界面: `NESettingsService.openBeautyUI()`
  - 获取当前美颜等级参数: `NESettingsService.getBeautyFaceValue()`
  - 设置美颜等级参数：`NESettingsService.setBeautyFaceValue(int level)`
* 新增切换摄像头开关入会配置：
  - `NEMeetingOptions.noSwitchCamera`
* 新增切换音频模式开关入会配置：
  - `NEMeetingOptions.noSwitchAudioMode`
* 新增SIP拨号入会 

####  新增特性

* 废弃`com.netease.meetinglib.sdk.NEMeetingMenuItem`菜单类，使用`com.netease.meetinglib.sdk.menu.NEMeetingMenuItem`代替
* 废弃`NEMeetingOnInjectedMenuItemClickListener.onInjectedMenuItemClick(Context, NEMeetingMenuItem, NEMeetingInfo)`回调，使用`NEMeetingOnInjectedMenuItemClickListener.onInjectedMenuItemClick(Context , NEMenuClickInfo, NEMeetingInfo, NEMenuStateController)`代替

####  问题修复

* 视频镜像优化
* 入会前后横竖屏切换逻辑优化

#### v1.3.1 (2020-11-13)

####  新增特性

* 观看屏幕共享时支持手势缩放
* 新增SSOToken登录、自动登录
  - SSOToken登录：`NEMeetingSDK.loginWithSSOToken(String ssoToken, NECallback<Void> callback)`
  - 自动登录：`NEMeetingSDK.getInstance().tryAutoLogin(NECallback<Void> callback)`
* 支持配置会议内“会议号”显示规则
  - 配置项：`NEMeetingOptions.meetingIdDisplayOptions`
* 支持配置画廊模式开关
  - 配置项：`NEMeetingOptions.noGallery`



#### v1.3.0 (2020-10-29)

####  新增特性

* 新增画廊模式
* 新增结束会议添加断网提示
* 新增会议私有化部署
  - 开启私有化配置：`NEMeetingSDKConfig.useAssetServerConfig` 
* 新增获取会议账号信息方法
  - `NEAccountService.getAccountInfo()`
* 支持企业客户自定义个人会议短号
  - 会议短号获取：`NEAccountInfo.shortMeetingId`
  - 邀请里面包含了短号字段 `shortId`

####  新增特性

* 个人会议号获取方式变更
  - `NEAccountInfo.meetingId`
* 屏幕共享文案调整
* 删除会议转场页面取消按钮
* 状态栏适配优化
* 会中视觉优化调整

####  问题修复

* 修复会议显示时长偏差
* 优化屏幕共享过程中正在讲话逻辑

####  删除

* `NEMeetingInfo.getPersonalMeetingId`

--------

#### v1.2.6 (2020-09-29)

####  新增特性

* `NEMeetingSDKConfig.NEForegroundServiceConfig`新增配置会议时显示前台服务
* `NEAuthListener.onAuthInfoExpired`新增账号信息过期通知
* `NEMeetingCode.MEETING_DISCONNECTING_AUTH_INFO_EXPIRED`新增账号信息过期对应的会议退出码

---------

#### v1.2.5 (2020-09-24)

####  新增特性

* `NEMeetingSDKConfig.appName`增加配置入会应用名称
* `NEMeetingOptions.noMinimize`配置会议中是否允许最小化会议页面
* `NEMeetingStatus.MEETING_STATUS_INMEETING_MINIMIZED`新增会议最小化状态 
* `NEMeetingSDK.getControlService()`新增遥控器服务
* `NEControlService.openControlUI`打开遥控器
* `NEControlService.setOnCustomMenuItemClickListener`设置遥控器自定义点击事件 
* `NEControlService.registerControlListener`注册监听遥控器回调
* `NEControlService.unRegisterControlListener`反注册监听遥控器回调
* `NEControlService.getCurrentMeetingInfo`获取当前会议详情。如果当前无正在进行中的会议，则回调数据对象为空

-------

### v1.2.3 (2020-09-18)

####  新增特性

* `NEJoinMeetingParams.password`新增密码入会字段
* `NEMeetingStatus.MEETING_STATUS_WAITING`新增会议等待状态
* `NEMeetingCode.MEETING_WAITING_VERIFY_PASSWORD`新增会议等待状态类型 
* `NEMeetingInfo.password、subject、startTime、endTime`新增会议信息字段
* `NEMeetingSDK.NEPreMeetingService`新增预约会议服务
* `NEPreMeetingService.scheduleMeeting` 新增预定会议
* `NEPreMeetingService.cancelMeeting`新增取消已预定的会议
* `NEPreMeetingService.getMeetingItemById`新增查询预定会议信
* `NEPreMeetingService.getMeetingList`新增查询特定状态下的会议列表
* `NEPreMeetingService.registerScheduleMeetingStatusListener`新增注册预定会议状态变更监听器
* `NEPreMeetingService.unRegisterScheduleMeetingStatusListener`新增反注册预定会议状态变更监听器 

-------

#### v1.2.0 (2020-09-04)

####  新增特性

* `MeetingServiceListener增加onInjectedMenuItemClick:meetingInfo:`添加自定义菜单按钮监听
* `NEMeetingService.getCurrentMeetingInfo`获取当前会议信息
* `NEMeetingOptions.noInvite`配置会议中是否显示"邀请"按钮 
* `NEMeetingOptions.noChat`配置会议中是否显示"聊天"按钮
* `NEMeetingOptions#injectedMoreMenuItems"更多"菜单中的自定义注入菜单项

-------

#### v1.1.0 (2020-09-04)

####  新增特性

* `NEMeetingSDK.isInitialized()`查询SDK初始化状态
* `NEMeetingService.getMeetingStatus()`查询当前会议状态
* 会议设置服务`NEAccountService`用于保存和查询用户的相关会议选项

-------

####  v1.0.0 (2020-07-10)

####  新增特性

* 首次正式发布

  
