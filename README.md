<!Doctype html>
<!DOCTYPE html>
<html>
<head>
	<title>Create Update & Delete</title>
	<link rel="stylesheet" type="text/css" href="css/styles.css" />
	<script language="javascript" type="text/javascript">
	</script>
	<style>
		body {background-color:skyblue;
				margin-left:10px; 
				margin-right:10px;
				margin-top: 50px;
				margin-bottom: 10px;
		}
		table,tr,thead {border:2px solid black; 
						font-size: 20px 
						width:100px;
						}
		label
			{
			font-family:arial;
			font-size:10px;
			color: solid black;
			}
			a:link {
  					color: red;
  					background-color: blue; 
 					 border: none;
 					 color: white;
 		 			padding: 5px 5px;
 					 text-align: center;
 					 text-decoration: none;
 					 display: inline-block;
 					 font-size: 10px;
					}
		input[type=text] {
 				 width: 20%;
 				 padding: 10px 10px;
  				margin: 8px 0;
  				box-sizing: border-box;
  				font-size:10px;
				}
		button {
 		 background-color: blue; 
 		 border: none;
 		 color: white;
 		 padding: 10px 10px;
 		 text-align: center;
 		 text-decoration: none;
 		 display: inline-block;
 		 font-size: 14px;
		}				
	</style>
</head>

<body>
	<?php require_once 'process.php'; ?>

	<?php if (isset($_SESSION['messsage'])): ?>
		<div class="alert alert -<=$_SESSION['msg_type']?>">
				<?php
				echo $_SESSION['message'];
				unset($_SESSION['message']);
				?>
			</div>
		<?php endif ?>
			<div class="container">
	<?php
		$mysqli= new mysqli('localhost','root','','updel') or die(mysqli_error($mysqli));
		$result = $mysqli -> query("SELECT * FROM data") or die($mysqli->error);
		//result
		?>
	</div>
		<div class="row" align="center">
				<table class="table">
					<thead>
						<tr>
							<th>Name</th>
							<th>Location</th>
							<th colspan="2">Action</th>
						</tr>
					</thead>
			<?php
				while ($row = $result -> fetch_assoc()):
			?>
			<tr>
				<td><?php echo $row['name']; ?></td>
				<td><?php echo $row['location']; ?></td>
				<td>
					<a href="index.php?edit=<?php echo $row['id']; ?>" class = "btn btn-info">EDIT</a>
					<a  href="process.php?delete=<?php echo $row['id']; ?>" class ="btn btn-danger">DELETE</a>
				</td>
			</tr>
		<?php endwhile; ?>
				</table>
		</div>
		<?php
		function pre_r($array){
			echo '<pre>';
			print_r($array);
			echo '</pre>';
		}
	?>
	<div class="row" align="center">
	<form action = "process.php" method="POST">
		<input type="hidden" name="id" value="<?php echo $id; ?>">
		<div class="form-group" align="center">
		<label>Name</label>
		<input type="text" name="name" class="form-control" value="<?php echo $name; ?>" placeholder ="Enter name"required>
	</div>
	<div class="form-group">
		<label>Location</label>
		<input type="text" name="location" class="form-control" value="<?php echo $location; ?>" placeholder="Enter location"required>
	</div>
	<div class="form-group" align="center">
		<?php
		if($update == true):
	?>
			<button type= "submit" class="btn btn-primary" name="update">Update</button>
		<?php else: ?>
		<button type= "submit" class="btn btn-primary" name="save">Save</button>
	<?php endif; ?>
	</div>
	</form>
</div>
</body>
</html>


================================================================================================================================


<?php

session_start();

$mysqli = new mysqli('localhost', 'root', '', 'updel') or die(mysqli_error($mysqli));

$id = 0;
$update = false;
$name = '';
$location = '';

if (isset($_POST['save'])){
	$name = $_POST['name'];
	$location = $_POST['location'];

	$mysqli ->query("INSERT INTO data(name, location) VALUES('$name', '$location')") or die($mysqli->error);

	$_SESSION['message']= "Record has been saved.";
	$_SESSION['msg_type']="success";

	header("location: index.php");

}

if(isset($_GET['delete'])){
	$id = $_GET['delete'];
	$mysqli->query("DELETE FROM data WHERE id=$id") or die($mysqli->error());

	$_SESSION['message']= "Record has been deleted.";
	$_SESSION['msg_type']="danger";

	header("location: index.php");
}

if(isset($_GET['edit'])){
	$id = $_GET['edit'];
	$update =true;
	$result = $mysqli ->query("SELECT * FROM data WHERE id=$id") or die($mysqli->error());
	if (count($result)==1){
		$row = $result ->fetch_array();
		$name = $row['name'];
		$location = $row['location'];
	}
}

	if (isset($_POST['update'])){
		$id =$_POST['id'];
		$name= $_POST['name'];
		$location = $_POST['location'];

		$mysqli -> query("UPDATE data SET name='$name', location = '$location' WHERE id=$id") or die($mysqli->error);

		$_SESSION['message']= "Record has been updated.";
	$_SESSION['msg_type']="warning";

	header("location: index.php");
	}

