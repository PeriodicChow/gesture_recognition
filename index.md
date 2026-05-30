---
---

# 自我介绍

张老师您好，我是2025届人工智能专业本科生周齐翔，高中阶段有做过人工智能手势识别视力检测项目，积累了计算机视觉、模型部署等实战经验。我对手势识别等前沿方向有浓厚兴趣。

# 为什么对这个项目感兴趣

高中我做的课题就是手势识别下的视力检测系统，同样试图减轻医疗资源压力，与您的课题相契合。而且，我对于手势识别等前沿方向有浓厚兴趣，希望能在进入课题组后在您指导下掌握更多知识。

# Demo演示

该手势识别系统不仅实现了对于手部关节坐标的捕获与绘制，还通过关键特征识别出0到9数字手势
<iframe src="//player.bilibili.com/player.html?isOutside=true&aid=116664246997306&bvid=BV1TZVL6dEA6&cid=38728961975&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>

# 技术方案

- 定义`draw_hand_landmarks(frame, hand_landmarks, color=(0,255,0), thickness=2)`函数，传入手部各坐标，在每个关节点绘制实心圆并连接
- 定义`is_finger_extended(landmarks, finger: str)`函数，能够判断一根手指是否伸直
- 定义`recognize_gesture(hand_landmarks)`函数，识别手势返回数字，手势具有以下特征：
	- 8: 拇指与食指伸直，其他弯曲
	- 6: 拇指与小指伸直，其他弯曲
	- 5: 五指全部伸直
	- 4: 四指伸直，拇指弯曲
	- 3: 食、中、无名指伸直，小指和拇指弯曲
	- 2: 食、中指伸直，其他弯曲
	- 1: 只伸直食指
- 并且对于特殊手势如9，7，0做出区分:
	- 9: 食指弯曲呈钩状
	- 7: 中指食指拇指接触，无名指和小指弯曲
	- 0: 食指与大拇指指尖接触，其他伸直
- 手指伸直使用 MCP → TIP 距离与各节长度之和的比值，对拇指使用 IP 关节角度辅助判断。
- 手指接触直接坐标距离判断
- 捕捉摄像头，定义视频流，使用cv2转换为RGB通道，逐帧识别，调用`draw_hand_landmarks()`绘制连线
- github pages部署通过 Jekyll 将 `.md` 自动渲染为 `.html`
