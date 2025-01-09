# Enrollment-Management-System

Public Class Form2
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        Form1.Show()
        Me.Hide()

    End Sub
End Class


Imports System.Data.OleDb
Imports System.Data

Public Class Form1
    Dim connect As New OleDbConnection
    Dim command As OleDbCommand
    Dim sql As String = Nothing
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        connect.ConnectionString = "Provider=Microsoft.ACE.OLEDB.12.0;Data Source=|DataDirectory|\student.accdb;"



    End Sub

    Private Sub LinkLabel1_LinkClicked(sender As Object, e As LinkLabelLinkClickedEventArgs)


    End Sub

    Private Sub loginBtn_Click(sender As Object, e As EventArgs) Handles loginBtn.Click
        If connect.State = ConnectionState.Closed Then
            connect.Open()
        End If

        If username.Text = Nothing Or password.Text = Nothing Then
            MessageBox.Show("Please fill all blanks fields", "Error Message", MessageBoxButtons.OK, MessageBoxIcon.Error)
        Else
            sql = "SELECT *  FROM account WHERE username = ? and password = ?"


            command = New OleDbCommand(sql, connect)
            command.Parameters.AddWithValue("@1", OleDbType.VarChar).Value = username.Text
            command.Parameters.AddWithValue("@2", OleDbType.VarChar).Value = password.Text

            Dim check = Convert.ToInt32(command.ExecuteScalar())

            If check > 0 Then

                MessageBox.Show("Successfully Login!", "information Message", MessageBoxButtons.OK, MessageBoxIcon.Information)
                dashboard.Show()

                Me.Hide()

            Else

                MessageBox.Show("Wrong Username/Password", "Error Message", MessageBoxButtons.OK, MessageBoxIcon.Error)
            End If

        End If


    End Sub

    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        Me.Close()

    End Sub
End Class

Imports System.IO.File
Imports System.IO.FileStream
Public Class Dashboard
    Private Sub AddNewToolStripMenuItem_Click(sender As Object, e As EventArgs)


    End Sub

    Private Sub ComboBox1_SelectedIndexChanged(sender As Object, e As EventArgs) Handles ComboBox1.SelectedIndexChanged

    End Sub

    Private Sub Dashboard_Load(sender As Object, e As EventArgs) Handles MyBase.Load

    End Sub

    Private Sub Button5_Click(sender As Object, e As EventArgs) Handles Button5.Click
        RecordsBindingSource2.AddNew()

    End Sub

    Private Sub Button6_Click(sender As Object, e As EventArgs) Handles Button6.Click
        On Error GoTo SaveErr
        RecordsBindingSource2.EndEdit()
        RecordsTableAdapter.Update((Student_recordsDataSet.records))
        MessageBox.Show("Successfully Save!")

SaveErr:
        Exit Sub

    End Sub

    Private Sub Button7_Click(sender As Object, e As EventArgs) Handles Button7.Click
        RecordsBindingSource2.MovePrevious()

    End Sub

    Private Sub Button10_Click(sender As Object, e As EventArgs) Handles Button10.Click
        RecordsBindingSource2.MoveNext()

    End Sub

    Private Sub Button8_Click(sender As Object, e As EventArgs) Handles Button8.Click
        RecordsBindingSource2.MoveFirst()

    End Sub

    Private Sub Button9_Click(sender As Object, e As EventArgs) Handles Button9.Click
        RecordsBindingSource2.MoveLast()

    End Sub

    Private Sub Button4_Click(sender As Object, e As EventArgs) Handles Button4.Click
        OpenFileDialog1.ShowDialog()
        TextBox4.Text = OpenFileDialog1.FileName
    End Sub

    Private Sub TextBox4_TextChanged(sender As Object, e As EventArgs) Handles TextBox4.TextChanged
        If (System.IO.File.Exists(TextBox4.Text)) Then
            PictureBox1.Image = Image.FromFile(TextBox4.Text)
        End If

        If TextBox4.Text = "" Then
            PictureBox1.Hide()

        Else
            PictureBox1.Show()
        End If
    End Sub

    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        Form1.Show()
        Me.Hide()

    End Sub

    Private Sub Button3_Click(sender As Object, e As EventArgs) Handles Button3.Click
        subject2.Show()
        Me.Hide()

    End Sub

    Private Sub Button2_Click(sender As Object, e As EventArgs) Handles Button2.Click
        Student_Overview.Show()
        Me.Hide()
    End Sub
End Class

Imports System.IO.File
Imports System.IO.FileStream
Public Class Dashboard
    Private Sub AddNewToolStripMenuItem_Click(sender As Object, e As EventArgs)


    End Sub

    Private Sub ComboBox1_SelectedIndexChanged(sender As Object, e As EventArgs) Handles ComboBox1.SelectedIndexChanged

    End Sub

    Private Sub Dashboard_Load(sender As Object, e As EventArgs) Handles MyBase.Load

    End Sub

    Private Sub Button5_Click(sender As Object, e As EventArgs) Handles Button5.Click
        RecordsBindingSource2.AddNew()

    End Sub

    Private Sub Button6_Click(sender As Object, e As EventArgs) Handles Button6.Click
        On Error GoTo SaveErr
        RecordsBindingSource2.EndEdit()
        RecordsTableAdapter.Update((Student_recordsDataSet.records))
        MessageBox.Show("Successfully Save!")

SaveErr:
        Exit Sub

    End Sub

    Private Sub Button7_Click(sender As Object, e As EventArgs) Handles Button7.Click
        RecordsBindingSource2.MovePrevious()

    End Sub

    Private Sub Button10_Click(sender As Object, e As EventArgs) Handles Button10.Click
        RecordsBindingSource2.MoveNext()

    End Sub

    Private Sub Button8_Click(sender As Object, e As EventArgs) Handles Button8.Click
        RecordsBindingSource2.MoveFirst()

    End Sub

    Private Sub Button9_Click(sender As Object, e As EventArgs) Handles Button9.Click
        RecordsBindingSource2.MoveLast()

    End Sub

    Private Sub Button4_Click(sender As Object, e As EventArgs) Handles Button4.Click
        OpenFileDialog1.ShowDialog()
        TextBox4.Text = OpenFileDialog1.FileName
    End Sub

    Private Sub TextBox4_TextChanged(sender As Object, e As EventArgs) Handles TextBox4.TextChanged
        If (System.IO.File.Exists(TextBox4.Text)) Then
            PictureBox1.Image = Image.FromFile(TextBox4.Text)
        End If

        If TextBox4.Text = "" Then
            PictureBox1.Hide()

        Else
            PictureBox1.Show()
        End If
    End Sub

    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        Form1.Show()
        Me.Hide()

    End Sub

    Private Sub Button3_Click(sender As Object, e As EventArgs) Handles Button3.Click
        subject2.Show()
        Me.Hide()

    End Sub

    Private Sub Button2_Click(sender As Object, e As EventArgs) Handles Button2.Click
        Student_Overview.Show()
        Me.Hide()
    End Sub
End Class


Public Class Student_Overview
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        Dashboard.Show()
        Me.Hide()

    End Sub

    Private Sub Button2_Click(sender As Object, e As EventArgs) Handles Button2.Click
        PictureBox1.Image = My.Resources._2021_2022

    End Sub

    Private Sub Button3_Click(sender As Object, e As EventArgs) Handles Button3.Click
        PictureBox1.Image = My.Resources._2022_2023
    End Sub

    Private Sub Button4_Click(sender As Object, e As EventArgs) Handles Button4.Click
        PictureBox1.Image = My.Resources._2023_2024
    End Sub

    Private Sub Button5_Click(sender As Object, e As EventArgs) Handles Button5.Click
        PictureBox1.Image = My.Resources._2024_2025
    End Sub

    Private Sub Label2_Click(sender As Object, e As EventArgs) Handles Label2.Click

    End Sub
End Class


