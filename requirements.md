# 项目“就它了”需求文档

## 项目概述
**项目名称**: 就它了 (Pick It)
**定位**: 解决外卖点餐者的选择困难症痛点
**核心价值**: 将“更多选择”转换为“唯一选择”
**目标平台**: iOS & Android (跨平台)
**项目状态**: 需求收集与设计阶段

## 用户场景与痛点
- **用户痛点**: 在美团、淘宝闪购、京东秒送等平台面对众多餐厅和菜品时不知如何选择
- **目标用户**: 学生、上班族、有选择困难症的外卖用户
- **核心场景**: 用户打开外卖App时感到迷茫，需要一个简单直接的决策辅助工具

## 功能需求

### 1. 新用户注册引导
- **基础偏好设置**:
  - 询问用户是否最近在保持身材
- **菜系偏好设置** (两步走方案):
  
  #### 第一步：选择喜欢的菜系
  - **页面文案**: "平时爱吃什么菜？选几个你最常吃的（可多选）"
  - **选择方式**: 多选，最多5个
  - **菜系列表** (22类):
    
    | 菜系类别 | 代表菜品 | 常见忌口项 |
    |----------|----------|------------|
    | 川菜 | 麻婆豆腐、水煮鱼、回锅肉、辣子鸡 | 麻辣、花椒、重油、内脏 |
    | 湘菜 | 剁椒鱼头、小炒黄牛肉、辣椒炒肉 | 辛辣、腊味、烟熏 |
    | 粤菜 | 白切鸡、烧腊、虾饺、肠粉 | 偏甜、清淡（部分人嫌太淡） |
    | 江浙菜（淮扬菜） | 红烧肉、松鼠鳜鱼、糖醋排骨 | 偏甜、酱油重、河鲜 |
    | 东北菜 | 锅包肉、地三鲜、猪肉炖粉条 | 重油、咸口、分量大 |
    | 西北菜（清真） | 大盘鸡、羊肉串、拉条子 | 羊肉、面食、孜然 |
    | 鲁菜 | 九转大肠、葱烧海参、把子肉 | 内脏、咸鲜、葱蒜重 |
    | 闽菜 | 佛跳墙、荔枝肉、沙茶面 | 海鲜、沙茶酱、偏甜 |
    | 徽菜 | 臭鳜鱼、毛豆腐、胡适一品锅 | 发酵味、重咸、内脏 |
    | 云南菜 | 过桥米线、汽锅鸡、野生菌火锅 | 菌类、酸辣、香料特殊 |
    | 港式茶餐厅 | 菠萝包、干炒牛河、丝袜奶茶 | 中西混合、分量偏小 |
    | 台湾菜 | 卤肉饭、蚵仔煎、牛肉面 | 甜咸口、海鲜 |
    | 日料 | 寿司、拉面、天妇罗、刺身 | 生食、海鲜、芥末 |
    | 韩餐 | 泡菜汤、炸鸡、石锅拌饭 | 辣、发酵味、蒜味重 |
    | 泰餐 | 冬阴功汤、咖喱蟹、芒果糯米饭 | 酸辣、鱼露、椰浆（部分人不喜） |
    | 西餐（美式） | 汉堡、披萨、牛排 | 芝士、生食、油炸 |
    | 西餐（意式） | 意面、披萨、烩饭 | 芝士、番茄底、橄榄 |
    | 快餐/简餐 | 炸鸡、汉堡、薯条 | 油炸、高热量 |
    | 粉面类 | 牛肉面、螺蛳粉、酸辣粉 | 特定粉类（如螺蛳粉臭味）、辣 |
    | 粥品类 | 皮蛋瘦肉粥、海鲜粥 | 皮蛋、内脏、海鲜 |
    | 烧烤/炸串 | 烤串、炸串 | 烟熏味、重调料、内脏 |
    | 轻食/沙拉 | 鸡胸沙拉、波奇饭 | 生冷、酱汁、牛油果 |
    | 甜品/饮品 | 奶茶、蛋糕、糖水 | 过甜、乳糖不耐 |

  #### 第二步：选择绝对不吃的忌口
  - **页面文案**: "有什么是绝对不碰的？选得越准，推荐越靠谱"
  - **选择方式**: 多选，不限数量
  - **忌口分类展示**:
    
    **1. 食材类忌口**
    - 不吃辣
    - 不吃猪肉
    - 不吃牛肉
    - 不吃羊肉
    - 不吃内脏（心肝肺肠等）
    - 不吃海鲜（鱼虾蟹贝）
    - 不吃菌类
    - 不吃豆制品
    - 不吃香菜/葱/蒜（香料类）
    - 不吃生食（刺身、生腌）

    **2. 口味/做法类忌口**
    - 不吃太咸
    - 不吃太甜
    - 不吃太油
    - 不吃酸
    - 不吃麻（花椒）
    - 不吃油炸
    - 不吃烟熏/烧烤味

  - **交互设计**: 使用"药丸式"按钮，点选即可，不用长列表滚屏

### 2. 轻度选择困难症模式
- **推荐机制**: 每次点餐推荐3家店的菜品
- **交互页面设计**:
  - 每天首次打开App时，推荐一道菜（基于用户偏好+历史反馈）
  - 提供两个按钮:
    - **就它了** (确认选择)
    - **换一个** (获取新推荐)
- **推荐逻辑**: 基于用户偏好、历史反馈、餐厅评分等因素

### 3. 重度选择困难症模式
- **推荐机制**: 每次点餐只显示1家店的菜品
- **交互页面设计**:
  - 每天首次打开App时，显示唯一推荐（无换菜按钮）
  - 只有一个按钮: **接受挑战**
- **积分激励系统**:
  - 积分规则: 下单金额1元 = 1积分
  - 积分用途: 兑换虚拟奖品
  - 奖品类型: 外卖红包优惠券、视频会员等

### 4. 推荐算法需求
- **输入因素**:
  - 用户基础偏好（菜系选择、身材保持状态）
  - 历史订单数据
  - 用户反馈（喜欢/不喜欢）
  - 餐厅评分与口碑
  - 配送距离与时间
  - 价格区间
- **输出**: 个性化菜品推荐

### 5. 用户反馈机制
- 每次推荐后收集用户反馈
- 记录用户选择（就它了/换一个/接受挑战）
- 基于反馈调整推荐权重

## 非功能需求

### 1. 性能需求
- 推荐结果加载时间 < 2秒
- App启动时间 < 3秒
- 支持并发用户数: 初期1000，可扩展

### 2. 安全需求
- 用户数据加密存储
- 支付/积分系统安全
- 防止恶意刷积分行为

### 3. 兼容性需求
- iOS 12+ 兼容
- Android 8.0+ 兼容
- 支持主流屏幕尺寸

### 4. 可维护性需求
- 模块化代码结构
- 清晰的API文档
- 自动化测试覆盖

## 技术栈建议

### 前端
- **框架**: React Native (跨平台iOS/Android)
- **状态管理**: Redux或MobX
- **UI组件库**: React Native Paper或自定义组件
- **导航**: React Navigation

### 后端
- **语言**: Node.js (Express/NestJS) 或 Python (FastAPI)
- **数据库**: 
  - PostgreSQL (主数据存储)
  - Redis (缓存、会话管理)
- **推荐算法**: Python (scikit-learn, pandas) 或 Node.js + TensorFlow.js
- **API风格**: RESTful API 或 GraphQL

### 基础设施
- **云服务**: AWS/GCP/Azure 或国内云服务（阿里云/腾讯云）
- **CI/CD**: GitHub Actions
- **监控**: Sentry, LogRocket

### 第三方服务
- **用户认证**: Firebase Auth 或 自建JWT
- **推送通知**: Firebase Cloud Messaging
- **数据分析**: Google Analytics 或 自建
- **支付集成**: 微信支付、支付宝（积分兑换）

## 数据模型（详细设计）

### 用户表 (Users)
- id (主键, UUID)
- username (用户名)
- email (邮箱, 唯一)
- phone (手机号, 唯一)
- password_hash (密码哈希)
- weight_watching (boolean, 是否在保持身材)
- created_at (创建时间)
- updated_at (更新时间)
- last_login_at (最后登录时间)

### 菜系表 (Cuisines)
- id (主键, 整数)
- name (菜系名称, 如"川菜")
- description (描述)
- icon (图标URL或本地资源名)
- popularity_score (默认受欢迎度分数, 0-100)
- created_at

### 菜系代表菜品表 (CuisineDishes)
- id (主键)
- cuisine_id (外键)
- dish_name (菜品名称, 如"麻婆豆腐")
- is_popular (是否热门代表菜)
- created_at

### 忌口表 (DietaryRestrictions)
- id (主键)
- name (忌口名称, 如"不吃辣")
- category (分类: 'ingredient'食材类 / 'taste'口味做法类)
- description (描述)
- severity_level (严重程度: 1-5, 5表示绝对不能碰)

### 用户菜系偏好表 (UserCuisinePreferences)
- id (主键)
- user_id (外键)
- cuisine_id (外键)
- preference_type (enum: 'liked'喜欢 / 'neutral'中性 / 'disliked'不喜欢)
- preference_weight (权重: 0.0-1.0, 喜欢=1.0, 中性=0.5, 不喜欢=0)
- selected_at (选择时间)

### 用户忌口表 (UserDietaryRestrictions)
- id (主键)
- user_id (外键)
- restriction_id (外键)
- is_absolute (是否绝对忌口, true=绝对不能碰, false=尽量少碰)
- created_at

### 餐厅表 (Restaurants)
- id (主键)
- name (餐厅名称)
- address (地址)
- latitude (纬度)
- longitude (经度)
- average_price (人均价格)
- rating (评分, 1-5)
- delivery_time (平均配送时间, 分钟)
- cuisine_ids (菜系ID数组, JSON)
- is_active (是否营业中)
- created_at
- updated_at

### 菜品表 (Dishes)
- id (主键)
- restaurant_id (外键)
- name (菜品名称)
- description (描述)
- price (价格)
- cuisine_id (主菜系)
- secondary_cuisine_ids (次要菜系, JSON数组)
- dietary_tags (忌口标签, JSON数组, 如["spicy", "pork"])
- popularity_score (受欢迎度分数)
- is_available (是否可售)
- image_url (图片URL)
- created_at
- updated_at

### 推荐历史表 (RecommendationHistory)
- id (主键)
- user_id (外键)
- dish_id (外键)
- restaurant_id (外键)
- recommendation_type (enum: 'light'轻度模式 / 'heavy'重度模式)
- recommended_at (推荐时间)
- user_action (enum: 'accepted'就它了 / 'rejected'换一个 / 'challenged'接受挑战 / 'ignored'忽略)
- feedback_score (反馈评分, 1-5, 可选)
- session_id (会话ID, 用于追踪一次推荐会话)

### 积分表 (UserPoints)
- id (主键)
- user_id (外键, 唯一)
- points_balance (当前积分余额)
- total_earned (累计获得积分)
- total_spent (累计消耗积分)
- last_updated (最后更新时间)

### 积分交易表 (PointTransactions)
- id (主键)
- user_id (外键)
- transaction_type (enum: 'earn_consume'消费获得 / 'earn_challenge'挑战完成 / 'spend_redeem'兑换消耗)
- amount (积分数量, 正数为获得, 负数为消耗)
- order_id (关联订单ID, 可选)
- dish_id (关联菜品ID, 可选)
- description (交易描述)
- created_at

### 虚拟奖品表 (VirtualPrizes)
- id (主键)
- name (奖品名称, 如"5元外卖红包")
- type (奖品类型: 'food_coupon'外卖红包 / 'video_membership'视频会员 / 'other'其他)
- points_cost (所需积分)
- stock (库存数量, -1表示无限)
- is_active (是否可用)
- validity_days (有效期天数)
- created_at
- updated_at

### 用户奖品兑换表 (UserPrizeRedemptions)
- id (主键)
- user_id (外键)
- prize_id (外键)
- points_spent (消耗积分)
- redemption_code (兑换码)
- is_used (是否已使用)
- redeemed_at (兑换时间)
- used_at (使用时间)
- expires_at (过期时间)

## 开发阶段规划

### Phase 1: MVP (最简可行产品)
1. 用户注册与偏好设置
2. 轻度模式基本推荐（静态规则）
3. 简单的用户反馈收集
4. 基础UI界面

### Phase 2: 核心功能完善
1. 推荐算法实现（基于规则+简单机器学习）
2. 重度模式与积分系统
3. 用户行为分析与偏好学习
4. 优化UI/UX体验

### Phase 3: 生态扩展
1. 外卖平台API集成
2. 社交功能（分享推荐）
3. 高级个性化推荐
4. 商业化功能

## 成功指标
- **用户留存率**: 次日留存 > 40%，7日留存 > 20%
- **推荐准确率**: 用户接受推荐比例 > 60%
- **用户满意度**: 应用商店评分 > 4.5星
- **商业模式验证**: 积分兑换率 > 10%

---
*文档创建时间: 2026-03-27*
*最后更新: 2026-03-27 11:14*