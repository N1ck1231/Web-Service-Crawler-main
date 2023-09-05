本仓库来源于2022届本科毕业设计:
> 刘羽鑫. 基于ProgrammableWeb的Web服务爬虫系统. 湖南科技大学本科毕业论文. 2022. [PDF](2022_本科毕业论文_刘羽鑫.pdf), [Slides](2022_答辩PPT_刘羽鑫.pdf)  
> Email: 1376493805@qq.com
## 目录
- [系统组成](#系统组成)
- [版本配置](#版本配置)
- [系统使用说明](#系统使用说明)
  - [子系统crawlerData使用说明](#子系统crawlerData使用说明)
  - [子系统srb-abmin使用说明](#子系统srb-abmin使用说明)
  - [子系统crawler-system使用说明](#子系统crawler-system使用说明)
- [数据集字段描述](#数据集字段描述)
  - [API数据集](#API数据集)
  - [Mashup数据集](#Mashup数据集)
  - [SampleSourceCode数据集](#SampleSourceCode数据集)
  - [SDK数据集](#SDK数据集)
 
## <span id=" ">系统组成</span>
**Web爬虫系统分为三个子系统**
1. **crawlerData**：用Python代码写的爬虫程序，爬取的网站地址为: <https://www.programmableweb.com/>
2. **srb-abmin**：Vue框架搭建的前端项目
3. **crawler-system**：SpringBoot框架搭建的后端项目，前后端项目需要配合一起使用才能够达到展示数据的效果

## <span id=" ">版本配置</span>
| Package | Version | 
| :-----| :----- | 
| python | 3.10.2 | 
|beautifulsoup4| 4.10.0|
|configparser| 5.2.0|
|files| 1.1.1|
|openpyxl| 3.0.9|
|pandas| 1.4.2|
|properties| 0.6.1|
|pyinstaller-hooks-contrib|2022.2|
|python-dateutil|2.8.2|
|requests|2.27.1|
|urllib3|1.26.8|

**注**：以上Python包不一定均有使用,若有使用,版本则按上表所示.

## <span id=" ">系统使用说明</span>
### <span id=" ">子系统crawlerData使用说明</span>
- Step 1：使用Pyinstaller把程序打包成了.exe可执行文件
 ![image](https://user-images.githubusercontent.com/68261447/172369104-2d2526a9-ca74-464f-ba0e-5a5383ccd3c7.png)
- Step 2：点击crawlerData/dist/main/main.exe运行程序，得到的数据保存在crawlerData/dist/main/data目录下
 ![image](https://user-images.githubusercontent.com/68261447/172370369-b27f4105-45b3-4ccb-856d-f63f411b8167.png)

### <span id=" ">子系统srb-abmin使用说明</span>
 需要安装的软件：Node+WebStorm  
- Node的版本：
![image](https://user-images.githubusercontent.com/68261447/171337406-1a096250-4ba8-4c4b-bc1e-878504d122de.png)
- 需要自定义的地方：
![image](https://user-images.githubusercontent.com/68261447/171337805-ca6e31eb-25ac-453b-bc99-b29a922a06c1.png)
- Step 1：在终端界面数据npm install(需要提前安装Node)
- Step 2：安装完成之后会出现node_modules
![image](https://user-images.githubusercontent.com/68261447/171338401-8214a416-3b43-48de-9afd-20d224a64c35.png)
- Step 3：输入npm run dev运行项目，这个项目运行之后只有界面，可能不存在数据，如果需要数据的话需要把下面crawler-system也运行起来

### <span id=" ">子系统crawler-system使用说明</span>
 需要安装的软件：IDEA+MySQL+Redis+SQLyog（这个使用Navicat也行，这只是一个数据库的可视化工具）    
 数据库文件也在工具目录tool之内，自己在MySQL数据库导入tool文件夹中.sql后缀的文件即可（可以借助SQLyog等MySQL可视化工具导入更加便捷）  
 application.yml配置说明:  
  ![image](https://user-images.githubusercontent.com/68261447/171333984-d9537e77-eec2-46ad-bc13-85969324e45f.png)
  ![image](https://user-images.githubusercontent.com/68261447/171334158-6482d95c-ddd6-428d-ab55-989db6b69888.png)
- Step 1：打开Redis
  在Redis的安装目录下，有一个redis-server.exe的文件，点击就可以打开Redis  
![image](https://user-images.githubusercontent.com/68261447/171334268-0b7e05d6-01a8-49c4-b6d8-2056634f4faf.png)
- Step 2：在IDEA中打开crawler-system项目，然后点击运行
![image](https://user-images.githubusercontent.com/68261447/171334196-66f8a8a3-d9d7-4995-8846-2ea8facd5e96.png)
- Step 3：通过端口号即可访问数据
  示例：![image](https://user-images.githubusercontent.com/68261447/171336246-a0456111-51a5-4dab-9c2f-93ef01582fd4.png)
  在这个项目调用爬虫程序说明，我是通过执行脚本文件来执行的，脚本文件在resource/bat/run.bat    
  ![image](https://user-images.githubusercontent.com/68261447/171336438-fa25c2a6-13ff-49d7-92ed-53fd890d34f1.png)
  ![image](https://user-images.githubusercontent.com/68261447/171336514-3ad39aac-9ebd-406b-910f-78d5cb6daac3.png)
  需要修改一些路径  
  ![image](https://user-images.githubusercontent.com/68261447/171336690-63a6ed24-7802-455c-9366-5664a93cc685.png)
  ![image](https://user-images.githubusercontent.com/68261447/171336807-efe5d608-7604-4bfa-9ede-4a148196d031.png)

## <span id=" ">数据集字段描述</span>
### <span id=" ">API数据集</span>
|  字段名 | 描述 |
|  :----  | :----  |
| api_name | API名称 |
| description | API文本描述 |
| categories | API类别 |
| submitted_date | API创建日期 |
| developers_numbers | 开发者数量 |
| developers_name | 对应的开发者名称 |
| developers_m_r | API参与开发的Mashup / Resource |
| followers_numbers | 关注者数量 |
| followers_name | 对应的关注者名称 |
| versions | API版本 |

### <span id=" ">Mashup数据集</span>
|  字段名 | 描述 |
|  :----  | :----  |
| mashups_name | Mashup名称 |
| related_apis | 相关联的API名称 |
| description | Mashup文本描述 |
| categories | Mashup的类别 |
| mashup_app_type | Mashup的类型 |
| company | 开发公司名称 |
| followers_numbers | 关注者数量 |
| followers_names | 对应的关注者名称 |
| submitted_date | Mashup创建日期 |

### <span id=" ">SampleSourceCode数据集</span>
|  字段名 | 描述 |
|  :----  | :----  |
| Name of Sample Source Code | Sample Source Code名称 |
| Description | Sample Source Code文本描述 |
| Related APIs | Sample Source Code对应的API |
| Related Platform / Languages | 使用的平台或编程语言 |
| Categories | Sample Source Code的类别 |
| Added Date | Sample Source Code发布日期 |
| Sample Source Code Provider | Sample Source Code提供商 |
| Followers Number | 关注者数量 |
| Followers | 对应的关注者名称 |
| Versions | 版本 |

### <span id=" ">SDK数据集</span>
|  字段名 | 描述 |
|  :----  | :----  |
| SDK Name | SDK名称 |
| Description | SDK文本描述 |
| Related APIs | SDK对应的API |
| Related Platform / Languages | 使用的平台或编程语言 |
| Categories | SDK的类别 |
| Added Date | SDK发布日期 |
| SDK Provider | SDK提供商 |
| Followers Number | 关注者数量 |
| Followers | 对应的关注者名称 |


