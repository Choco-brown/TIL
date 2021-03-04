
## 태그 간 차이점 구별하기
#  Select - option vs datalist - option


### Select - option

-   Select 태그의 옵션 목록
    
    -   select 키워드에 옵션을 입력하여 리스트를 제한할 수 있다
        
    -   multiple : 여러 값을 선택할 수 있게 함
        
    -   size : 화면에 보여질 목록의 개수 지정
        
    -   disabled : 화면에는 보이지만 수정할 수 없도록 비활성화
        
    -   selected : 화면에 초기 값으로 보여질 목록 선택
        
-   Select 태그는 option 태그 외에 <optgroup>도 사용 가능하다
    
    > ※ _optgroup_ : 목록에 그룹을 지정해 줄 수 있는 태그( ex) 그룹 1 - 목록1, 목록2)
    
-   드롭다운 형식으로 보여지고, 리스트중 선택하는 방식을 사용
    

```
<select size = "1" >
	<optgroup label = "그룹 1">
		<option> 목록 1 </option>
		<option> 목록 2 </option>
		<option> 목록 3 </option>
	</optgroup>
	<optgroup label = "그룸 2">
		<option > 목록 4 </option>
		<option> 목록 5 </option>
	</optgroup>
	<option> 목록 1 </option>
	<option> 목록 2 </option>
	<option> 목록 3 </option>
</select>
```

### **Datalist - option**

-   입력창에 텍스트를 입력하면 유사한 키워드 목록을 보여준다.
-   Select 태그와 달리 Datalist의 옵션은 따로 지원되지 않으며 option 태그만 사용 가능
-   텍스트 필드 형태로 보여짐
>   html5 부터 키워드를 입력하면 자동완성으로 리스트를 보여줄 수 있다!

```
지역 선택하기
        <input type = "text" list = "location">
        <datalist id = "location">
            <option label = "Seoul">서울 특별시</option>
            <option label = "Busan">부산 광역시</option>
            <option label = "Daegu">대구 광역시</option>
            <option label = "Gwanju">광주 광역시</option>
            <option label = "Incheon">인천 광역시</option>
            <option label = "Daejeon">대전 광역시</option>
            <option label = "Gyeonggi-do">경기도</option>
            <option label = "Gangwon-do">강원도</option>
        </datalist>
```
