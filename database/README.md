﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿**Interface documents ：**

使用database模块的用户只需关心database.api.Operator.get\_result( self , given )函数即可，实例化一个Operator对象，通过调用其get\_result函数完成对数据库的操作。
##
####database.api.Operator.get_result ( self , given)  参数，返回值与异常说明:
#####Arguments:
+ given: 一个dict对象，要求格式如下
+ given={"function"：操作码，  
"content"：要求传入数据，根据操作码所定 }
#####Return：
+ res:一个dict对象，格式如下
+ res={ "success": True or False ,  
"message"：传递的基本消息，用于日志记录,  
"content"：从数据库获取的数据，根据操作码所定}
#####Raise：
暂未进行测试
##
####操作码对应要求传入数据，返回数据以及意义:

#####GET\_USER\_BY\_NAME  1:
+ 根据用户名称检索用户数据
+ given["content“]:dict对象，要求具有value为用户名，key为name的键
+ res["content"]:dict对象，用户信息，key和value的对应关系可见database.models.model.UserInfo，查询失败时为None

#####INSERT\_USER : 2
+ 插入用户
+ given["content“]:dict对象，要求具有所有用户信息的键，key和value的对应关系可见database.models.model.UserInfo
+ res["content"]:None

#####DELETE\_USER\_BY\_NAME : 3
+ 删除用户
+ given["content“]:dict对象，要求具有value为用户名，key为name的键
+ res["content"]:None

#####UPDATE\_USER\_PWD : 4
+ 更新用户密码
+ given["content“]:dict对象，要求具有value为用户名，key为name以及value为新密码，key为password的键
+ res["content"]:dict对象，用户信息，key和value的对应关系可见database.models.model.UserInfo，查询失败时为None

#####GET\_RECOMMEND\_QUESTION : 5
+ 获取推荐问题列表
+ given["content“]:dict对象，要求具有value为问题数量，key为number的键
+ res["content"]:list对象，list中的每一个元素都为dict对象，存储问题信息，key和value的对应关系可见database.models.model.QuestionInfo

#####GET\_USER\_FOLLOW : 6
+ 获取用户关注的问题列表
+ given["content“]:dict对象，要求具有value为问题数量，key为number的键
+ res["content"]:list对象，list中的每一个元素都为dict对象，存储问题信息，key和value的对应关系可见database.models.model.QuestionInfo

#####INSERT\_QUESTION : 7
+ 插入问题
+ given["content“]: dict对象，要求具有所有问题信息的键，key和value的对应关系可见database.models.model.QuestionInfo
+ res["content"]:NONE

#####GET\_QUESTION\_BY\_ID  8:
+ 根据问题id检索问题
+ given["content“]:dict对象，要求具有value为问题id，key为quid的键
+ res["content"]:dict对象，问题信息，key和value的对应关系可见database.models.model.QuestionInfo，查询失败时为None

#####INSERT\_QUESTION : 9
+ 插入问题
+ given["content“]: dict对象，要求具有所有答案信息的键，key和value的对应关系可见database.models.model.AnswerInfo
+ res["content"]:NONE

#####GET\_ANSWER\_BY\_ID  10:
+ 根据问题id检索问题
+ given["content“]:dict对象，要求具有value为答案id，key为ansid的键
+ res["content"]:dict对象，问题信息，key和value的对应关系可见database.models.model.AnswerInfo，查询失败时为None

#####GET\_ANSWER\_BY\_QUID : 11
+ 获取问题的所有答案
+ given["content“]:dict对象，要求具有value为问题id，key为quid的键
+ res["content"]:list对象，list中的每一个元素都为dict对象，存储答案信息，key和value的对应关系可见database.models.model.AnswerInfo

#####GET\_QUESTION\_BY\_UID : 12
+ 获取用户提出的所有问题
+ given["content“]:dict对象，要求具有value为用户id，key为uid的键
+ res["content"]:list对象，list中的每一个元素都为dict对象，存储问题信息，key和value的对应关系可见database.models.model.QuestionInfo

#####GET\_ANSWER\_BY\_UID : 13
+ 获取问题的所有答案
+ given["content“]:dict对象，要求具有value为用户id，key为uid的键
+ res["content"]:list对象，list中的每一个元素都为dict对象，存储答案信息，key和value的对应关系可见database.models.model.AnswerInfo

#####DELETE\_ANSWER\_BY\_ID : 14
+ 删除答案
+ given["content“]:dict对象，要求具有value为答案id，key为ansid的键
+ res["content"]:None

#####DELETE\_ANSWER\_BY\_ID : 15
+ 删除问题
+ given["content“]:dict对象，要求具有value为问题id，key为quid的键
+ res["content"]:None

#####INSERT\_FOLLOW : 16
+ 添加关注
+ given["content“]:dict对象，要求具有value为用户id，问题id，key为uid，quid的键
+ res["content"]:None

#####DELETE\_FOLLOW : 17
+ 删除关注
+ given["content“]:dict对象，要求具有value为用户id，问题id，key为uid，quid的键
+ res["content"]:None

#####INSERT\_CATEGORY : 18
+ 添加分类
+ given["content“]:dict对象，要求具有value为分类id，分类名称，key为catid，catname的键
+ res["content"]:None

#####INSERT\_CATEGORY : 19
+ 删除分类
+ given["content“]:dict对象，要求具有value为分类id，key为catid的键
+ res["content"]:None

#####GET\_ALL\_CATEGORY : 20
+ 获取所有分类信息
+ given["content“]:None
+ res["content"]:dict对象，key为分类id，value为分类名称

#####GET\_QUESTION\_BY\_CAT : 21
+ 获取指定分类的问题
+ given["content“]:dict对象，要求具有value为问题数量，分类id，key为number，catid的键
+ res["content"]:list对象，list中的每一个元素都为dict对象，存储问题信息，key和value的对应关系可见database.models.model.QuestionInfo


####
####PS:用户名，密码等属性的类型（String，Integer......)见database.models.model.py
####











>>>>>>> upstream/develop
