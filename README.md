# 橙 狐 (OFRP) for Xiaomi Pad 5 Pro 12.4 (dagu)  
使用小米平板 5 Pro 12.4 ，HyperOS（安卓14）制作，适用于橙狐安卓12分支  

![OFRP](https://image.ibb.co/cTMWux/logo.jpg "OFRP")  

参考来自[ymdzq](https://github.com/ymdzq/OFRP-device_xiaomi_elish.git)的修改

====================================================
# 目前进度
屏幕画面显示花屏，无法使用，看logcat日志: 0 E         : [drm:sde_encoder_underrun_callback:3816] [sde error]underrun: 11600 应该还是内核问题，连带触摸也有问题  


所以需要修改内核才能使用，不过我就这三脚猫能力目前不知道咋改内核
目前只能通过命令的方式  
# 如何使用
进入[Release](https://github.com/RainGreenleaf/OFRP-device_xiaomi_dagu/releases)下.img用工具临时刷入
# 如何构建
下载OFRP源代码，克隆这个仓库放到相应的位置  
例如OFRP源代码根目录为~/fox_12.1，则保存为~/fox_12.1/device/xiaomi/dagu/:  
```bash
mkdir -p /fox_12.1/device/xiaomi
cd /fox_12.1/device/xiaomi
git clone https://github.com/RainGreenleaf/OFRP-device_xiaomi_dagu.git dagu
```
打开源代码根目录运行:  
```bash
. build/envsetup.sh && lunch twrp_dagu-eng && mka bootimage
```
# 云编译
利用Github Action在线编译橙狐  
例如你的 Github 用户名是 "JohnSmith"  
1. 打开[橙狐Action编译器](https://github.com/carlodandan/OrangeFox-Action-Builder)仓库，然后在新页面点击右上角的`Fork`按钮  
![image](https://user-images.githubusercontent.com/37921907/177914706-c92476c5-7e14-4fb3-be94-0c8a11dae874.png)
2. 等待网页自动重定向后，你将会看到你的用户名下的新仓库  
![image](https://user-images.githubusercontent.com/37921907/177915106-5bde6fc9-303c-479e-b290-22b48efd1e4e.png)
3. 网页上方进入 `Actions` 页面 > `All workflows` > `OrangeFox - Build` > `Run workflow`  
![image](https://user-images.githubusercontent.com/37921907/177915304-8731ed80-1d49-48c9-9848-70d0ac8f2720.png)
4. 按照以下内容填写参数  
OrangeFox Branch  
`12.1`  
Custom Recovery Tree  
`https://github.com/RainGreenleaf/OFRP-device_xiaomi_dagu.git`  
Custom Recovery Tree Branch  
`fox_12.1-a14`  
Specify your device path.  
`device/xiaomi/dagu`  
Specify your Device Codename.  
`dagu`  
Specify your Build Target  
`boot`  
![image](https://user-images.githubusercontent.com/37921907/177915346-71c29149-78fb-4a00-996f-5d84ffc9eb8c.png)
5. 填写完毕后, 点击 "Run workflow" 开始运行
6. 编译结果可以在你Fork后的新仓库的Release页面下载
