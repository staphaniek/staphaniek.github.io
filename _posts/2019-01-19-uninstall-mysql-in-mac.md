---
layout: post
title: "맥에서 mysql 삭제하기"
comments: true
---

mac OS에서 터미널이 아닌 installer로 mysql을 설치한 후 나오는 임시 비밀번호를 무심코 넘겨버려서 mysql에 들어갈 수 없는 상황이 일어났었습니다. 이 비밀번호를 알 방법이 없을까 찾아봐도 저의 부족한 구글링 실력으로는 알 방법이 없었습니다. <br>
정신승리를 하자면 어차피 회사에서 사용하는 mysql 버전과는 동떨어진 버전을 설치했더라구요 ㅋㅋ 그래서 결국은 mac에서 mysql을 삭제하게 되었습니다. 혹시나 잘못 설치할 일이 다시 생길 것 같아서 그 때 했던 뻘짓을 기록해두려고 합니다.<br>
아래 과정을 차례대로 terminal에 입력하면 mysql이 삭제됩니다.
```bash
sudo rm -rf /usr/local/var/mysql
sudo rm -rf /usr/local/bin/mysql*
sudo rm -rf /Library/StartupItems/MySQLCOM
sudo rm -rf /Library/PreferencePanes/My*
```
그 후 `vim /etc/hostconfig`을 통해 들어가서 `MYSQLCOM=-YES-` 이 줄을 지웁니다.
```bash
rm -rf ~/Library/PreferencePanes/My*
sudo rm -rf /Library/Receipts/mysql*
sudo rm -rf /Library/Receipts/MySQL*
sudo rm -rf /var/db/receipts/com.mysql.*
```
(Library들은 OS version이 올라가면서 없어진것 같기도...?)<br>
잘 기억은 안나는데 이 이후에 컴을 재부팅하거나 터미널을 껐다가 켜야하나 했던 것 같습니다. 혹시나 다음에 삭제하게 되면 확인해서 수정해놓을게요.<br>
이렇게 하면 mysql을 지울 수 있고, 다시 brew 등을 통해 원하는 버전을 설치하면서 임시 비밀번호를 기억해놓으면 되지 않을까 싶습니다. 사실 처음에 잘 설치하는게 제일 좋긴 하지만요...
