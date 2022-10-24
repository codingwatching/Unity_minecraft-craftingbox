#                 #### 마인크래프트 제작대 ####
![캡처화면2](https://user-images.githubusercontent.com/77636255/115140267-720aef80-a071-11eb-984f-d29fa7cadb50.PNG)
# 목차
* [소개](#소개)
* [구현 내용](#구현-내용)

## 소개
* Unity 3D 2018 4.14 Ver.
* 2022/10/24 마우스 버그 수정과 전체적인 코드 리팩토링

## 구현 내용
* [아이템 슬롯](#아이템-슬롯)
* [마우스 좌클릭](#마우스-좌클릭)
* [마우스 우클릭](#마우스-우클릭)
* [아이템 제작](#아이템-제작)
* [전체적인 코드의 흐름](#전체적인-코드의-흐름)
___

### 아이템 슬롯
* 3종류의 아이템 슬롯을 ENUM으로 제작해 변수로 갖도록 함
* DROP = 인벤토리, CRAFT = 제작대, OUTPUT = 제작해서 나오는 아이템 슬롯
```
    public enum SlotType
    {
        DROP =  1,
        CRAFT = 2,
        OUTPUT = 3
    };
    public SlotType slotType = SlotType.DROP;
```
* 유니티 마우스 터치, 클릭 이벤트를 이용해 slot과 아이템의 정보를 가져도록 함
```
    public void OnPointerEnter(PointerEventData eventdata)
    {
        // 슬롯 정보 가져오기
        ClickManager.GetInstance.slot = gameObject;
    }

    public void OnPointerExit(PointerEventData eventdata)
    {
        // 슬롯 정보 초기화
        ClickManager.GetInstance.slot = null;
    }
```
```
 public void OnPointerDown(PointerEventData _eventData)
 {
    if(ClickManager.GetInstance.clickItem == null)
    {
        // 아이템의 정보를 가져온다.
        ClickManager.GetInstance.clickItem = gameObject; 
    }
 }
```
