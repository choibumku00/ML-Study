## **Matplotlib 기초**

사진이 안보여서 노션 링크도 올립니다.  
https://www.notion.so/bumku/ML-AI-study-20c093a01001472e9773d2c360e3db75
---
1. 그래프 그리기 (x, y좌표 이용)

```python
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([0, 6]) # y개수에 맞춰 입력해주면됨
ypoints = np.array([0, 250]) 

plt.plot(xpoints, ypoints)
plt.show()
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4836f13e-d421-4a21-8e69-5d3316d545a5/Untitled.png)

2. 그래프 그리기 (y좌표 이용)

```python
ypoints = np.array([3, 8, 1, 10, 5, 7]) # 자동으로 x=1부터 1씩 증가

plt.plot(ypoints)
plt.show()
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9021e101-75c6-4cc3-aea9-3176a55a08a4/Untitled.png)

3. 그래프 데이터 꾸미기

```python
plt.plot(ypoints, marker = 'o:r') # o는 점 찍기 :는 점선 r은 빨간색
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/adb65fd4-50c9-4f82-a126-620e2e4d7dc5/Untitled.png)

4. 그래프 두개 출력

```python
# 방법1 x,y좌표 둘다 주기
x1 = np.array([0, 1, 2, 3])
y1 = np.array([3, 8, 1, 10])
x2 = np.array([0, 1, 2, 3])
y2 = np.array([6, 2, 7, 11])

plt.plot(x1, y1, x2, y2)

# 방법2 y좌표만 주기
y1 = np.array([3, 8, 1, 10])
y2 = np.array([6, 2, 7, 11])

plt.plot(y1) # 이 경우는 따로따로 plot해야함 2개 한번에 하면 x,y로 인식
plt.plot(y2)
```

5. 라벨 및 제목

```python
plt.title("Sports Watch Data", loc = 'left') # 상단 제목을 왼쪽에 붙임
plt.xlabel("Average Pulse") # x축 라벨
plt.ylabel("Calorie Burnage") #y축 라벨
```

6. 눈금 표시

```python
plt.grid() # x,y축으로 눈금 표시
plt.grid(axis = 'x') # x축 눈금 표시
plt.grid(axis = 'y') # y축 눈금 표시
```

7. 여러개의 그래프 표시

```python
#subplot은 어디에 그래프를 그릴지 설정

x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(2, 3, 1) # 2행 3열중 1번째에 그래프 그리기
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(2, 3, 2) # 2행 3열중 2번째에 그래프 그리기
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(2, 3, 3) # 2행 3열중 3번째에 그래프 그리기
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(2, 3, 4) # 2행 3열중 4번째에 그래프 그리기
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(2, 3, 5) # 2행 3열중 5번째에 그래프 그리기
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(2, 3, 6) # 2행 3열중 6번째에 그래프 그리기
plt.plot(x,y)

# plt.suptitle("MY SHOP") # 입력할 경우 전체의 제목 생성
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fbb60d67-48c4-4d1a-9499-028c35dd74a7/Untitled.png)

8. 데이터 점으로만 표시

```python
x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])

plt.scatter(x, y) # plt.plot(x, y, 'o')와 비슷

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
colors = np.array(["red","green","blue","yellow","pink","black","orange","purple","beige","brown","gray","cyan","magenta"])

plt.scatter(x, y, c=colors) # 색갈도 추가 가능
```

9. 데이터 바 형식으로 표시

```python
x = np.array(["A", "B", "C", "D"])
y = np.array([3, 8, 1, 10])

plt.bar(x,y) # 가로로 바를 하고 싶으면 plt.barh(x, y) 사용, 가로축은 x
plt.show()
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc221db8-f446-4e4f-84db-5f860b7a2bc0/Untitled.png)

10. 히스토그램

```python
x = np.random.normal(170, 10, 250) # 170값에 집중된 표준 편차가 10인 250개 데이터 생성

plt.hist(x)
plt.show()
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2ef9840c-9ccd-4477-bfe6-fbec25b1306c/Untitled.png)

11. 파이 차트

```python
y = np.array([35, 25, 25, 15]) # 차지할 영역 표시 상대적인 비율로 표시함
mylabels = ["Apples", "Bananas", "Cherries", "Dates"] 
myexplode = [0.2, 0, 0, 0] # 눈에 띄게 중앙에서 떨어지게 하기

plt.pie(y, labels = mylabels, explode = myexplode, shadow = True)
# 라벨을 mylables로 표시함 #explode를 myexplode로 설정
#그림자를 줌
plt.legend(title = "Four Fruits:") #옆에 데이터의 정보를 나타냄 title은 없어도 됨
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ad8e683f-459e-4883-8cf8-a7d64ad8f16b/Untitled.png)
