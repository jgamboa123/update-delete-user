readme.md
# updatedelete



// Update

<!DOCTYPE html>
<html>
<head>
	<title>Update </title>
	<link rel="stylesheet" type="text/css" href="update.css" />
</head>
<body>
<div style="width:523px; margin: 0 auto; margin-top: 100px;"  align="center">
	<div class="header_title"><h1>Update User</h1></div>

<div>
	<table border="0" cellpadding="10" cellspacing="0" width="500" align="center" class="table_wrapper">
		<tr>
			<td>
				<table border="0" cellpadding="10" cellspacing="0" width="500" align="center" class="inner_table">
					<tr>
						<td><label>First Name</label></td>
						<td><input type="text" name="firstname[]" class="field" value=""required></td>
					</tr>
					<tr>
						<td><label>Last Name</label></td>
						<td><input type="text" name="lastname[]" class="field" value=""required></td>
					</tr>
					<tr>
						<td><label>Username</label></td>
						<td>
							<input type="text" name="username[]" class="field" value=""required></td>
					</tr>
					<tr>
						<td><label>Password</label></td>
						<td><input type="password" name="password[]" class="field" value=""required></td>
					</tr>
				</table>
				</div>
			</td>
		</tr>
	</div>
					<tr>
						<td colspan="2" align="center"><input type="submit" name="submit" value="Save Changes" class="button"></td>
					</tr>
					</div>
					</table>
</form>
<div align="center" class="button" onClick="window.location.replace('LOGIN.HTML')">Back</div>

</div>
</body>
</html>


//==============================================================================================================================//


//delete


<!DOCTYPE html>
<html lang="en">
<head>
	<title> Delete an Account</title>
	<meta charset="utf-8">
	<link rel="stylesheet"  href="delete.css">	
</head>
<body>
<div style="width:523px; margin: 0 auto; margin-top: 100px;"  align="center">
	<div class="header-title"><h1> Delete </h1></div>
	</div>
	<div class="form-group">
	<table  border="0" cellpadding="10" cellspacing="0" width="500" align="center" class="inner_table">
						<tr>
						<td><label>Username</label></td>
						<td>
							<input type="hidden" name="userId[]" class="field" value="">
							<input type="text" name="username[]" class="field" value=""required></td>
					</tr>
					<tr>
						<td><label>Password</label></td>
						<td><input type="password" name="password[]" class="field" value=""required></td>
					</tr>
						<tr>
						<td><label>Confirm Password</label></td>
											<td>	<input type="password" name="password []" class="field"value =""required></td>

						</tr>
						</table>
					</div>
					<div class="form-group" align="center">
						<input type="submit" name="submit" class="btn btn-primary" value="submit"a href="submit"></a>
					</div>
			
					<div align="center" class="btn btn-primary" onClick="window.location.replace('LOGIN.HTML');">Back</div>
</body>
</html>
