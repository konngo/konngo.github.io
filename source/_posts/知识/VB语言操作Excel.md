title: VB语言操作Excel
date: '2019-06-11 16:29:35'
updated: '2019-08-07 14:26:17'
tags: [excel, vb]
permalink: /articles/2019/06/11/1560241775522.html
---
## 单元格内指定字段变为红色

```vb
Sub changeColor()
	Dim rng As Range,istart%,ilen%
	With Sheet1.[a1].currentRegion
For Each rng In .Offset(0,0)
If Len(rng) Then
	istart=InStr(rng,"__|")+3
	ilen=InStr(rng,"|nome|")-istart
	If istart>5 Then 
		rng.Characters(istart,ilen).Font.ColorIndex=3
	End If
End If
Next
End With
Application.ScreenUpdating=true
Set rng=Nothing
End Sub
```

>  1.在Sheet1这个表格页面中，遍历a1附近边缘是任意空行和空列组合成的范围。
>  2.istart :单元格内出现该字段的开始位置；ilen：该字段的长度 （该字段结束位置-开始位置）
>  3.将该字段的字体颜色ColorIndex设置为3（红色）。