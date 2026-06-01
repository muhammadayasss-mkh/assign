<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>

<!DOCTYPE html>
<html>
<head runat="server">
    <title>All Controls + Validation</title>
</head>
<body>
<form id="form1" runat="server">

    <h2>Basic Controls + President Election Form</h2>

    <!-- ===== BASIC CONTROLS ===== -->

    <h3>Basic Controls</h3>

    <!-- Button -->
    <asp:Button ID="btnClick" runat="server" Text="Click Me" OnClick="btnClick_Click" />
    <br /><br />

    <!-- DropDownList -->
    Select Course:
    <asp:DropDownList ID="ddlCourse" runat="server">
        <asp:ListItem>--Select--</asp:ListItem>
        <asp:ListItem>BCA</asp:ListItem>
        <asp:ListItem>B.Com</asp:ListItem>
        <asp:ListItem>B.Sc</asp:ListItem>
    </asp:DropDownList>
    <br /><br />

    <!-- ListBox -->
    Select City:
    <asp:ListBox ID="lstCity" runat="server">
        <asp:ListItem>Chennai</asp:ListItem>
        <asp:ListItem>Kumbakonam</asp:ListItem>
        <asp:ListItem>Trichy</asp:ListItem>
    </asp:ListBox>

    <br /><br />
    <asp:Label ID="lblResult" runat="server" ForeColor="Blue"></asp:Label>

    <hr />

    <!-- ===== PRESIDENT ELECTION FORM ===== -->

    <h3>President Election Form</h3>

    <!-- Name -->
    Name:
    <asp:TextBox ID="txtName" runat="server"></asp:TextBox>
    <asp:RequiredFieldValidator ID="rfvName" runat="server"
        ControlToValidate="txtName"
        ErrorMessage="Name required"
        ForeColor="Red" />
    <br /><br />

    <!-- Age -->
    Age:
    <asp:TextBox ID="txtAge" runat="server"></asp:TextBox>
    <asp:RequiredFieldValidator ID="rfvAge" runat="server"
        ControlToValidate="txtAge"
        ErrorMessage="Age required"
        ForeColor="Red" />
    <asp:RangeValidator ID="rvAge" runat="server"
        ControlToValidate="txtAge"
        MinimumValue="35"
        MaximumValue="100"
        Type="Integer"
        ErrorMessage="Age must be between 35 and 100"
        ForeColor="Red" />
    <br /><br />

    <!-- Email -->
    Email:
    <asp:TextBox ID="txtEmail" runat="server"></asp:TextBox>
    <asp:RegularExpressionValidator ID="revEmail" runat="server"
        ControlToValidate="txtEmail"
        ValidationExpression="\w+@\w+\.\w+"
        ErrorMessage="Invalid Email"
        ForeColor="Red" />
    <br /><br />

    <!-- Gender -->
    Gender:
    <asp:RadioButtonList ID="rblGender" runat="server">
        <asp:ListItem>Male</asp:ListItem>
        <asp:ListItem>Female</asp:ListItem>
    </asp:RadioButtonList>

    <br /><br />

    <!-- Submit -->
    <asp:Button ID="btnSubmit" runat="server" Text="Submit Form" OnClick="btnSubmit_Click" />

    <br /><br />
    <asp:Label ID="lblFinal" runat="server" ForeColor="Green"></asp:Label>

</form>
</body>
</html>


using System;

public partial class _Default : System.Web.UI.Page
{
    protected void btnClick_Click(object sender, EventArgs e)
    {
        lblResult.Text = "Course: " + ddlCourse.SelectedValue + 
                         ", City: " + lstCity.SelectedValue;
    }

    protected void btnSubmit_Click(object sender, EventArgs e)
    {
        if (Page.IsValid)
        {
            lblFinal.Text = "Form Submitted Successfully!";
        }
    }
}
