# ibox_api以及hook脚本

fridahook抓包脚本:

Java.perform(function() {
    var clz = Java.use('com.ibox.libs.common.utils.security.EncryptSecurityTool');
    var wxcloudCore=Java.use("com.tencent.wxcloud.WXCloudCore")
    wxcloudCore.callContainer.implementation=function(arg1,arg2,arg3,arg4,arg5){
        console.log("===========================================================")
        console.log(arg2)
        console.log(arg3)
        console.log(arg4)
        console.log("加密后===>",arg5)
        console.log("===========================================================")
        return this.callContainer(arg1,arg2,arg3,arg4,arg5)
    }
    clz.c.implementation = function(data,key) {
        console.log("+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++")
        console.log("明文===>" + data);
        console.log("加密key===>" + key);
        console.log("+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++")
        var result = this.c(data,key);
        return result;
    }})
    
    


ibox 接口列表，欢迎补充
# 网关算法购买请联系 vx: irabbit666
协议头：
{x-cloudbase-phone=, IB-DEVICE-ID=00000000-5217-9005-ffff-ffffef05ac4a_ad, IB-APP-VERSION=1.1.11, User-Agent=iBoxApp209, IB-PLATFORM-TYPE=android, HOST=api-app-tgw.ibox.art, language=zh-CN, Accept-Language=zh-CN, Content-Type=application/json; charset=UTF-8, IB-TRANS-ID=e4cbab2b-cf89-4a3c-a92d-edbc7b5f3e1b_android}

盲盒购买
POST
/nft-mall-web/v1/nft/blind/order/create
明文===>{"gId":"","num":"1","payChannel":"24","id":"100514484","type":0}

GET
/nft-mall-web/v1.2/nft/product/getCollectionListByUidV3?uid=12376016&onSale=0&pageSize=20&page=1&type=0

GET
/nft-mall-web/v1.2/nft/product/getBrandList?pageSize=50&sort=0&page=1

GET
/nft-mall-web/v1.2/nft/recommend/list?recommendType=2

GET
/nft-mall-web/v1/nft/order/list?pageSize=20&page=1&type=0

GET
/nft-mall-web/v1.1/nft/blind/getDynamic

GET
/nft-mall-web/v1.2/nft/product/getAlbumSearch?classifyId=&pageSize=20&page=1&order=0

GET
/nft-mall-web/nft/sand/getPayChannelList?gId=102090139&type=1

GET
/nft-mall-web/v1.2/nft/product/getProductDetail?albumId=100514223

GET
/nft-mall-web/v1/nft/blind/state?id=100514169

GET
/nft-mall-web/v1.2/nft/blind/list?onSaleTime=0&size=50&fromId=0&direction=1

GET
/nft-mall-web/v1.2/nft/blind/order/list?size=6&albumId=100514169&fromId=0&direction=1&operationTime=0

盲盒列表
GET
/nft-mall-web/v1.2/nft/blind/list?onSaleTime=0&size=20&fromId=0&direction=1

寄售升序列表
GET
/nft-mall-web/v1.2/nft/product/getResellList?classifyId=&origin=0&pageSize=20&sort=1&page=1&type=0

GET
/nft-mall-web/v1.2/nft/product/getProductDetail?gId=102090139&albumId=100513880

GET
/nft-mall-web/v1/nft/order/detail?orderId=11edf0ad604b413c90a7c1f67b082921

搜索
GET
/nft-mall-web/v1.2/nft/product/searchGoodsV2?captcha_id=0486d8f6864f45ea945ddcd9fa7a3a62&gen_time=1658740773&pageSize=50&sort=0&type=0&captcha_output=Mjq68xpNBN95B5ifvEjzZDAO9Ew2wiyjk9HimDb6h_O0g7FrhkPY0ERg9ZsckPthnjsIAwhFJn_9gVfFoc008hCkct_-ZNZJ9LgJuAhUWss3AIrq9V0K_afs_4JDwYWxtcPcBzyqAIgLtO-FqVW0mMzdSs_OYDswRfrBzKBKW_1i5lT8S3UoCm9HvBH4X5IC5UTnqtJPL_5v9y6PEdm5mg%3D%3D&content=box&lot_number=ebcd0e891a904600a04e97fe0aa49bf0&grade=-1&captcha_key=b4e013a741f3d0bbab4b6ac3f46e581d&onSale=1&subType=0&page=1&pass_token=7f4c146254744a75aafee02fa769c9b291c2dcb4c413f95006d1f9d66a8d1798

发送验证码
POST
/nft-mall-web/nft/user/sendSMSCode?captcha_id=da26d6425ee7156417b3557d9ef22e9a&gen_time=1658739916&captcha_key=e812308dbdb21c413229a740e8668256&captcha_output=Wr7wH383khY77j2fZm4Bh9EktKa2gXrK9nK4YgFfWfiWTPt5b7toGOYFmor3FRI8Yfc6AQdrTHnwIZTAM_F8k9sjqvB97wyWQ3DYPgyaRvw86tEv9iUibRAuTt2zDQgDyAC4V83qWUNZi0nGEkqvRm54r0t8wZ3cQ2q3TROoZI1uU2K4hjwRQYNRLTbkTz-tagpmlPXo-LIDQInlGhDIlWwdwGrQEZmwklpoy43CTmE%3D&pass_token=02fb94013a8cbf7d86cd8c9e96e19e6152aa003ad5e165714fd67465e32abf30&lot_number=1722a39860404df5aff8e4a0d4d32235

明文:{"phoneNumber":"19999999999"}

登录
POST
/nft-mall-web/v1.1/nft/user/login

明文:{"phoneNumber":"19999999999","code":"123456","inviteCode":""}

获取用户信息
POST
/nft-mall-web/v1.1/nft/user/getUserInfo

明文:""

验证token
POST
/nft-mall-web/nft/user/checkToken
直接发送===> {"token":"xxxxjqU7EeEgT9VpEhQ+NdXrRZJ8TEgOQtb9B1RBQZc="}

下单
POST
/nft-mall-web/v1/nft/order/create?captcha_id=89639f0a604fe5a0c95f08edf29b3441&gen_time=1658740893&captcha_key=a3dda6e4d08a1c1f46441ab2fc909a8f&captcha_output=OLmFN0iaIftQd0EG8_MwMYau_PHQLjbandrJIFnK33PJizZkDWttdJEOkUFxzEr6p1Ygnda-RDpouP6nkONz4TSYAJwVTEPQRMtwIx5ybV4XvpaRzTInC0gfSWHtAEzXum3JWGwMZ-aAAdx-I39GYTYrGPFqfZCf4_EiG-RZ8g1kDVhFW3fZxqtTj0LcT4eLsA45hKdk7nS9UW_dhRAeeQ%3D%3D&pass_token=0a4010349e83b2ad4f666fc3187658d2c42adf9ac80f39a09c758371e246b409&lot_number=b5001417a317400dadb939d99bbc6fcb

优先购
/nft-mall-web/nft/order/create?captcha_id=6bcc18dc7ecf5e296948b32a64b21ba2&gen_time=1658817021&captcha_output=fcFK39jIhY9RPWGY8e5pQ3bXOqAft45Zl_CJha3Qqb2qyjycFgzmWKFo9tyyT89itpMRrf-6vB4EvkRI014F99392Q_hWDzzcKwxkmssfCQTIFPGutv1O6xAF2_L7qWqcVofha_86olvKRtKczCMjrWHYz5KZL_D8SdZiylKi74Rjb-ZWK0kcvbdMqFJAhFe5Vk0YzqCIDoyZZt2w5g15Q%3D%3D&pass_token=72c0ba1b0c7390facb927317d985bee1193fd699bfe8c107ec8e48fbfec7c2e3&lot_number=30a26ca6ba9143f98fa5d2b29edf02ab

明文===>{"gId":"102090139","price":"769.0","albumId":"100513880","payChannel":"23","type":0,"gNum":"75504"}

合成：

/nft-mall-web/nft/product/syntheticNewGoods
POST明文：
{activityId:123,ids:[1,2,3]}

取消订单
POST
/nft-mall-web/nft/order/cancle
明文===>{"orderId":"xxedf0ad604b413c90a7c1f67b082921"}
