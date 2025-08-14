## 1) VBA 코드 만들기

### 1.Alt + F11 → VBA 편집기 열기

### 2.삽입 → 모듈 클릭

### 3.아래 코드 붙여넣기

```js
Function RegexExtract(ByVal txt As String, ByVal pattern As String) As String
    Dim re As Object, matches As Object
    Set re = CreateObject("VBScript.RegExp")
    re.Pattern = pattern
    re.IgnoreCase = True
    re.Global = False

    If re.test(txt) Then
        Set matches = re.Execute(txt)
        RegexExtract = matches(0).Value
    Else
        RegexExtract = ""
    End If
End Function
```

## 2) Excel에서 사용

```js
=RegexExtract(C1, "([가-힣]+)\s([가-힣0-9]+)\s(\d{3}-\d{4}-\d{4})")
```

정규식을 활용한 데이터추출
