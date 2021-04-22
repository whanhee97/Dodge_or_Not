# Dodge_or_Not

100MB 넘는 파일 에러 관계로 아래의 사이트를 참고하여 주세요
http://khuhub.khu.ac.kr/2016104156/dodge_or_not


***

## 프로젝트 설명
Riot Games에서 제공하는 API를 통해 리그오브레전드 정보를 알려주는 프로젝트입니다.   

이 프로젝트는 기존 FindMe.gg( http://khuhub.khu.ac.kr/MotherProject/Open_Source_Project.git )라는 마더 프로젝트를
개선하여 제작된 프로젝트입니다.

### 마더 프로젝트에서 개선된 점

1. CSS를 통한 디자인이 추가
2. 챔피언 사진을 클릭하면 챔피언 정보를 나타내는 공식 홈페이지로 이동
3. 소환사 최근 100게임 통계(선호하는 챔피언, 선호하는 라인) 추가
4. 최근 10게임 전적 추가

### 설치 방법

#### 1. Clone 하기    
```git clone <SSH>```   
```git clone <HTTP>```   
   
#### 2. pakage.json 다운로드   
/dodge_or_not/ 에서   
```npm install```

### 사용 방법

#### 1. ip 변수 설정해주기 (localhost에서 실행한다면 생략해도 됨)   

##### localhost에서 사용시
/dodge_or_not/RUTROLL/views/main.ejs 파일과   
/dodge_or_not/RUTROLL/views/index.ejs 파일 모두   
스크립트 태그에 ip변수를 "localhost"로 변경하십시오. (기본으로 설정되어있음)   
```
<script>
    $(document).ready(function(){


      $("button#searchButton").click(function(){
        var name = $("input").val();
        //var ip = $("#searchButton").val(); //searchButton의 value(Test.js에서 아이피값을 받아 렌더링한 값을 넣어놓음)로 아이피를 가져온다
        //var ip = "52.86.146.142" // aws 퍼블릭 아이피
        var ip = "localhost" // 로컬호스트
        location.href = "http://"+ip+":3000/search/" + name;
      })
    });
 </script>
```
##### aws와 같은 클라우드 서비스 사용시
ip변수를 다음과 같이 변경하십시오.   
```
<script>
    $(document).ready(function(){


      $("button#searchButton").click(function(){
        var name = $("input").val();
        var ip = $("#searchButton").val(); //searchButton의 value(Test.js에서 아이피값을 받아 렌더링한 값을 넣어놓음)로 아이피를 가져온다
        //var ip = "52.86.146.142" // aws 퍼블릭 아이피
        //var ip = "localhost" // 로컬호스트
        location.href = "http://"+ip+":3000/search/" + name;
      })
    });
 </script>
```
#### 2. app.js 실행
/dodge_or_not/RUTROLL/ 에서   
```node app.js```

***

## 활용 가능한 데이터 `(API_KEY Required.)`

### `SUMMONER-V4`

> https://kr.api.riotgames.com/lol/summoner/v4/summoners/by-name/{summonerName}

- 소환사 닉네임 - `name`
- 소환사 레벨 - `summonerLevel`
- 소환사 정보 갱신 시각 - `revisionDate`
- 암호화된 소환사 아이디 - `id`
- 암호화된 계정 아이디 - `accountId`

### `CHAMPION-MASTERY-V4`

> https://kr.api.riotgames.com/lol/champion-mastery/v4/champion-masteries/by-summoner/{encryptedSummonerId}

- 챔피언 아이디 - `championId`
- 챔피언 숙련도 레벨 - `championLevel`
- 챔피언 숙련도 점수 - `championPoints`
- 챔피언 남은 숙련도 점수 - `championPointsUntilNextLevel` (5레벨에 0 고정)
- 마지막 플레이 시각 - `lastPlayTime`
- 챔피언 레벨 토큰 개수 - `tokensEarned` (5레벨 이후를 위한 토큰)
- 마지막 챔피언 레벨 이후의 숙련도 점수 - `championPointsSinceLastLevel`
- 소환사 아이디 - `summonerId` (암호화)

### `CHAMPION-V3`

> https://kr.api.riotgames.com/lol/platform/v3/champion-rotations

- 금주의 무료 챔피언 - `freeChampionIds`
- 뉴비를 위한 무료 챔피언 - `freeChampionIdsForNewPlayers`

### `MATCH-V4`

> https://kr.api.riotgames.com/lol/match/v4/matchlists/by-account/{encryptedSummonerId}

- 매치 아이디 - `match_id`
- 매치 챔피언 - `match_champ`
- 매치 라인 - `match_lane`
- 매치 역할 - `match_role`
- 매치 시즌 - `match_season`
- 선호 데이터 - `preferData`

> https://kr.api.riotgames.com/lol/match/v4/matches/{matchId}

- 게임 모드 - `gameMode`
- 게임 지속시간 - `gameDuration` 
- 해당 매치 플레이어 정보 - `player` 

***
## 실행 화면
### 메인화면
![1](https://user-images.githubusercontent.com/55576129/115745171-238d8600-a3ce-11eb-8089-32d4ce97cb09.PNG)
### 검색화면(프로필)
![2](https://user-images.githubusercontent.com/55576129/115745224-3011de80-a3ce-11eb-9b2f-98ccebbf1570.PNG)
메뉴바 클릭하면 해당 메뉴로 이동
![image](https://user-images.githubusercontent.com/55576129/115746636-71ef5480-a3cf-11eb-81aa-895b7af73dfb.png)

### 최근 10게임 전적
![3](https://user-images.githubusercontent.com/55576129/115745334-4b7ce980-a3ce-11eb-97d9-d8d036b97ae6.PNG)
### 챔피언 숙련도
![4](https://user-images.githubusercontent.com/55576129/115745420-60597d00-a3ce-11eb-8886-faf92a89a3f8.PNG)
챔피언 클릭하면 해당 챔피언 정보 사이트로 이동
![4-2](https://user-images.githubusercontent.com/55576129/115746763-921f1380-a3cf-11eb-930e-3c85098a372b.PNG)

### 로테이션 챔피언
![5](https://user-images.githubusercontent.com/55576129/115745472-6e0f0280-a3ce-11eb-866c-6efea1c766ce.PNG)
해당 챔피언 아이콘 위에 마우스 올려놓으면 이름 표시
![5-2](https://user-images.githubusercontent.com/55576129/115746800-9a774e80-a3cf-11eb-84bc-80ad2e6c4e40.PNG)
***

## AWS서버를 이용한 접속가능 (AWS가 만료 될시 접속불가)   
> www.dodgeornot.tk:3000

***

## 라이센스 
MIT License

Copyright (c) 2020 Dodge or Not

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

