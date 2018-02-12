# EMAIL-VALIDATION

SAMPLE CODING

Partial Class _Default
    Inherits System.Web.UI.Page


    Protected Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click
        Label2.Text = IsEmailValid(TextBox1.Text)
        If Label2.Text = "False" Then
            Label2.Text = "Invalid EMail id"
        Else
            Label2.Text = "Valid EMail id"
        End If
    End Sub
    Public Function IsEmailValid(ByVal email As String) As Boolean
        Dim chunks As String() = email.Split("@")
        If chunks.Length() <> 2 Then Return False

        If chunks(0).Length = 0 OrElse chunks(1).Length < 3 Then Return False

        If Not chunks(1).Contains(".") Then Return False

        If Not Char.IsLetter((chunks(0))(0)) Then Return False

        For Each c As Char In email
            If Not Char.IsLetter(c) AndAlso Not Char.IsNumber(c) AndAlso c <> "_" AndAlso c <> "." AndAlso c <> "@" Then Return False
        Next

        If email.Contains("..") OrElse email.Contains(".@") OrElse email.Contains("@.") OrElse email.Contains("._.") Then Return False

        If email.EndsWith(".") Then Return False


        'check 2 char before dot .
        Dim pos1 As Integer = email.IndexOf("@")
        Dim pos2 As Integer = email.IndexOf(".")
        Dim posval As Integer = pos2 - pos1
        If posval <= 2 Then
            Return False
        End If

        'Finally
        Return True




    End Function

End Class
