## Numpy 기초


1. 배열 생성

```python
import numpy as np #numpy라이브러리 불러오기

#대괄호만 추가 하면 차원이 증가 
arr = np.array(42) //0차원 배열

arr = np.array([1, 2, 3, 4, 5]) #1차원 배열

arr = np.array([[1, 2, 3], [4, 5, 6]]) #2차원 배열
```

2. 튜플 생성

```python
arr = np.array((1, 2, 3, 4, 5))
```

3. 배열 차원 알기

```python
print(arr.ndim)
```

4. 배열 차원 정해주기

```python
arr = np.array([1, 2, 3, 4], ndmin=5) #이경우 [[[[[1 2 3 4]]]]]가 생성
```

5. 인덱스 접근

```python
arr = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])

print(arr[0, 1, 2]) #기존 배열과 비슷한 방법으로 접근
# -1인덱스는 마지막 인덱스

#인덱스로 Slice
arr = np.array([1, 2, 3, 4, 5, 6, 7])

print(arr[1:5]) #1번 인덱스~ 4번 인덱스까지 출력, 기존 슬라이싱과 동일

#Step
arr = np.array([1, 2, 3, 4, 5, 6, 7])

print(arr[1:5:2]) # 1~4인덱스에서 2칸씩 출력

print(arr[::2]) # 처음부터 끝까지 2칸씩 출력
```

6. 데이터 타입 정해주기

```python
arr = np.array([1, 2, 3, 4], dtype='S') # 원래 int로 저장될것이 String으로 저장
```

### 데이터 타입

- `i` - integer
- `b` - boolean
- `u` - unsigned integer
- `f` - float
- `c` - complex float
- `m` - timedelta
- `M` - datetime
- `O` - object
- `S` - string
- `U` - unicode string
- `V` - fixed chunk of memory for other type ( void )

7. 복사 및 참조

```python
arr = np.array([1, 2, 3, 4, 5])

x = arr.copy() # 복사
y = arr.view() # 참조

#base는 실제 값이 따로 있는지 봐줌
print(x.base) # 복사 했으므로 x배열이 자기자신임 # None 출력
print(y.base) # 참조 했으므로 실제 배열이 있음 # [1, 2, 3, 4, 5] 출력
```

8. 배열 형태 확인하기

```python
arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])

print(arr.shape) # (2,4) 출력 2행 4열이라는 뜻
```

9. 배열 차원 및 차원 새로 만들기

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12])

newarr = arr.reshape(4, 3) #4행 3열 배열로 새로 만들어줌
#단, 크기와 개수가 딱 맞아야함
```

10. 배열 for-each문으로 출력

```python
arr = np.array([[1, 2, 3], [4, 5, 6]])

#방법1
for x in arr:
  for y in x: # x는 2차원 입장
    print(y) # y는 1차원 입장

#방법2
for x in np.nditer(arr): # 원소 하나씩 다 꺼내옴
  print(x)

#인덱스와 값 모두 가져오기
for idx, x in np.ndenumerate(arr):
  print(idx, x)
```

11. 두 배열 조합

```python
#1차원 배열로 합치기
arr1 = np.array([1, 2, 3])

arr2 = np.array([4, 5, 6])

arr = np.concatenate((arr1, arr2)) #[1, 2, 3, 4, 5, 6]

#2차원 배열로 합치기
arr1 = np.array([[1, 2], [3, 4]])

arr2 = np.array([[5, 6], [7, 8]])

arr = np.concatenate((arr1, arr2), axis=1) #[[1 2 5 6] [3 4 7 8]]
```

12. 배열 짜르기

```python
arr = np.array([1, 2, 3, 4, 5, 6])

# 3개의 배열로 자르기    # 배열의 길이가 딱 안떨어져도 알아서 잘라줌
newarr = np.array_split(arr, 3) # [array([1, 2]), array([3, 4]), array([5, 6])] 

#차원이 더 높을 경우
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9], [10, 11, 12], [13, 14, 15], [16, 17, 18]])
#2차원씩 끊어준다
newarr = np.array_split(arr, 3) # [array([[1, 2, 3], [4, 5, 6]]), array([[ 7,  8,  9], [10, 11, 12]]), array([[13, 14, 15], [16, 17, 18]])]
```

13. 탐색

```python
x = np.where(arr == 4) # 배열에 4가 있는 인덱스 출력 # 여러개일 경우 모두 찾아줌

x = np.searchsorted(arr, 7) # 이진 탐색을 통해 7이 들어간다면 어디 들어가는게 좋을지 찾아줌

# 여러개를 넣을려는 경우
arr = np.array([1, 3, 5, 7])

x = np.searchsorted(arr, [2, 4, 6]) # [1 2 3] 출력
```

14. 정렬

```python
arr = np.array([3, 2, 0, 1]) 

print(np.sort(arr)) # [0, 1, 2, 3]
```

15. 필터
```python
arr = np.array([41, 42, 43, 44])

filter_arr = arr > 42

newarr = arr[filter_arr]

print(filter_arr) # [False False  True  True] 출력
print(newarr) # [43 44] 출력
```
