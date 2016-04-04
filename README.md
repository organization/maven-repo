# maven-repo
- Organization Official Maven Repo
- 오가니제이션 공식 메이븐 레포

## 개발자들에게
- 오가니제이션 내부 개발자분들은 향후에 누킷개발시 별도 레포화를 통해서 lib폴더에 별도로 jar파일을 놓게하는 잉여짓이 없도록 합시다. 조금 복잡하긴해도 API화 햬야하는 플러그인들은 레포에 업로드해서 쓰는게 좋을 것 같아서, 별도로 만들어놓습니다 :P 아 물론 이 레포 아니더라도 별도로 생성하셔서 쓰셔도 무방할 것 같아요..! (레포 목록이 많아지긴 하겠지만..)

## 레포 사용방법
- 사용할 pom.xml에 아래와 같이 레포주소를 추가합니다.
```
<repositories>
 <repository>
  <id>organization</id>
   <url>https://github.com/organization/maven-repo/raw/master/</url>
 </repository>
</repositories>
  
<dependency>
 <groupId>[POM에 적힌 groupID]</groupId>
 <artifactId>[POM에 적힌 artifactId]</artifactId>
 <version>[POM에 적힌 version]</version>
 <scope>provided</scope>
</dependency>
```

## 레포 업로드 방법
- 1.이 레포를 다운받습니다. (Git 으로든 이클립스로든 Zip으로든)
```
(예: git clone https://github.com/organization/maven-repo.git)
```

- 2.이 프로젝트 파일의 물리주소를 갖춰놓습니다.
```
(예: c:\workspace\maven-repo)
```

- 3.업로드 하고자 하는 프로젝트 컴파일본(예 JAR)의 물리주소를 갖춰놓습니다.
```
(예: c:\workspace\MongoDBLib\target\MongoDBLib-1.0.2-SNAPSHOT.jar)
```

- 4.아래 명령어를 입력합니다.
```
명령어 포멧
mvn install:install-file -DgroupId=[pom에 쓴 그룹명] -DartifactId=[pom에 쓴 articaftId명] -Dversion=[pom에 쓴 버전명] -Dpackaging=[출력포멧명] -Dfile=[사전에 컴파일해놓은 jar파일의 위치] -DlocalRepositoryPath=[사전에 다운받아놓은 maven-repo의 물리주소]

명령어 실제 사용 예
mvn install:install-file -DgroupId=mongodblib -DartifactId=MongoDBLib -Dversion=1.0.2-SNAPSHOT -Dpackaging=jar -Dfile=/home/hm/workspace/MongoDBLib/target/MongoDBLib-1.0.2-SNAPSHOT.jar -DlocalRepositoryPath=/home/hm/workspace/maven-repo
```

- 5.GitHub에 내 릴리즈 파일을 추가한 레포를 업로드합니다.
```
예: 이클립스의 경우 GUI에서 커밋후 풀처리.
예: git add "maven-repo"
git commit -m "MongoDBLib Update"
git push -u origin master
```
