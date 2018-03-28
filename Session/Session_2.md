# 2018-03-26 세션 2차시


## 1. 파이썬 실습 : 거북이 게임 코드 뜯어보기 - 은숙


### 1) 실습코드
    import turtle as t # turtle 라이브러리 import
    import random # random 라이브러리 import

    score = 0       # 점수 저장하는 변수
    playing = False # 현재 게임이 플레이중인지 확인하는 변수

    te = t.Turtle() #악당 거북이(빨간색)
    te.shape("turtle")
    te.color("red")
    te.speed(0)
    te.up()
    te.goto(0,200)

    ts = t.Turtle() #먹이 (초록색 동그라미)
    ts.shape("circle")
    ts.color("green")
    ts.speed(0)
    ts.up()
    ts.goto(0,-200)

    def turn_right(): # 오른쪽으로 방향을 바꾼다.
        t.seth(0)
    def turn_up():  # 위로 방향을 바꾼다.
        t.seth(90)
    def turn_left():    # 왼쪽으로 방향을 바꾼다.
        t.seth(180)
    def turn_down():    # 아래로 방향을 바꾼다.
        t.seth(270)

    def start():    # 게임을 시작하는 함수
        global playing  # global 사용하여 전역변수 선언
        if playing == False:
            playing = True
            t.clear() # 거북이가 그린 그림을 모두 지우는 함수
            play() # play 함수 시작

    def play():
        global score    # 전역변수 score 를  사용
        global playing  # 전역변수 playing 을 사용
        t.fd(10) # 주인공 거북이 10만큼 앞으로 이동

        if random.randint(1,5)==3:  # 1~5 사이에서 뽑은 수가 3이면 (20% 확률)
            ang=te.towards(t.pos()) # 악당 거북이가 주인공 거북이를 쳐다보는 각도 재고
            te.seth(ang) # 그 각도 만큼 이동한다.
        speed=score+5 # 점수에 5를 더해서 속도를 올린다.

        if speed>15: # 속도가 15를 넘으면
            speed = 15 # 속도는 15로 고정 시킨다.
        te.fd(speed)    #속도만큼 앞으로 이동한다.

        if t.distance(te)<12:   # 주인공과 악당의 거리가 12보다 작으면
                                # 게임을 종료시킨다.
            text = "Score : "+str(score)    # 점수 출력
            message('Game Over',text)   # Game over 출력
            playing = False # 게임 초기화
            score = 0   # 점수 초기화

        if t.distance(ts) <12: #주인공과 먹이의 거리가 12보다 작으면
            score = score+1 #점수를 올린다.
            t.write(score)  # 점수를 화면에 표시한다.
            star_x = random.randint(-230,230)
            star_y = random.randint(-230,230)
            ts.goto(star_x,star_y)  # 먹이를 다른 곳으로 옮긴다.

        if playing: # 게임이 플레이 중이면 0.1초 후 play 함수를 실행한다.
            t.ontimer(play,100)

    def message(m1,m2): # message 를 띄우는 함수
        t.clear()
        t.goto(0,100)
        t.write(m1,False,'center',('',20))# m1 내용을 움직이지 않고 가운데에 폰트 적용안하고 20pt 로 작성
        t.goto(0,-100)
        t.write(m2,False,'center',('',15))
        t.home() #거북이가 원점으로 돌아가고 오른쪽을 바라보는 기본 상태로 돌리는 함수


    t.title("Turtle Run") # title 을 보여준다.
    t.setup(500,500)    # 전체 크기를 처음에 500,500 으로 setting
    t.bgcolor('orange') # 배경색 설정
    t.shape('turtle')
    t.speed(0)
    t.up()
    t.color('white')
    t.onkeypress(turn_right,'Right')
    t.onkeypress(turn_up,'Up')  # 위쪽 키 누르면 turn_up
    t.onkeypress(turn_left,'Left')  # 왼쪽 키 누르면 turn_left
    t.onkeypress(turn_down,'Down')  # 아래쪽 키 누르면 turn_down
    t.onkeypress(start,'space') # space 키 누르면 start 실행
    t.listen() # 거북이 그래픽 창이 키보드 입력을 받도록 한다.
    message('Turtle Run','[space]') # 메시지를 표시한다.


### 2) 관련 링크 <http://blog.naver.com/PostView.nhn?blogId=angelrra&logNo=220829815805>


***


## 2. 파이썬 실습 : 파이썬 장고 프레임워크로 웹페이지 구현하기 (1) - 태중


### 1) 파이썬 설치
### 2) 파이참 설치
### 3) 장고 설치
* cmd 창 실행 후 아래 코드 입력
    pip install django
### 4) 파이썬 가상환경 구현
(1) cmd 창 실행 후 아래 코드 입력
    pip install virtualenv
(2) 가상환경 만들기
    virtual 가상환경이름/Scripts/activate
보통 가상환경이름은 venv로 한다.
(3) 생성된 가상환경 활성화하기
    가상환경이름/Scripts/activate
(4) 가상환경에 django 설치하기
    pip install django
### 5) 만든 가상환경에서 장고 프로젝트 시작하기
    django-admin startproject 프로젝트이름


✔ 여기서 나는 가상환경 활성화가 안됐다. 아마도 내 컴퓨터 이름이 한글로 되어 있는게 원인인 것 같다. 어떻게 해결해야하지...


### 6) 장고 구성 살펴보기
-> 다음 이 시간에...
