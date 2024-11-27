```
Sub doc2docx()
Dim myDialog As FileDialog, oFile As Variant
Set myDialog = Application.FileDialog(msoFileDialogFilePicker)
With myDialog
        .Filters.Clear    '清除所有文件筛选器中的项目
        '增加筛选器的项目为所有WORD2007文件
        .Filters.Add "所有 WORD2003 文件", "*.doc", 1    
        .AllowMultiSelect = True    '允许多项选择
        If .Show = -1 Then    '确定
		'在所有选取项目中循环 With Documents.Open(oFile)
        For Each oFile In .SelectedItems    
             
             With Documents.Open(oFile)
             .SaveAs FileName:=Replace(oFile, "doc", "docx"), FileFormat:=wdFormatDocumentDefault
             .Close
             End With
         Next
    End If
 End With
 End Sub
```
