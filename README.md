# Mac-KakaoTalk-Dual-Installation

# 카톡을 /Applications 경로에 넣고 실행해야한다. 
rm -rf /Applications/KakaoTalkDev.app
cp -a /Applications/KakaoTalk.app /Applications/KakaoTalkDev.app
mv /Applications/KakaoTalkDev.app/contents/MacOS/KakaoTalk /Applications/KakaoTalkDev.app/Contents/MacOS/KakaoTalkDev
cd /Applications/KakaoTalkDev.app/Contents/
sed -i .bak "s/KakaoTalk<\/string>/KakaoTalkDev<\/string>/g" Info.plist
sed -i .bak "s/com.kakao.KakaoTalkMac<\/string>/com.kakao.KakaoTalkDevMac<\/string>/g" Info.plist
codesign --force --deep --sign - /Applications/KakaoTalkDev.app
mv /Applications/KakaoTalkDev.app /Applications/KakaoTalkNew.app
open /Applications/KakaoTalkNew.app

