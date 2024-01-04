<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RESULTS</title>

    <style>
        .text{
            text-align:center;
            border:1px solid red;
            width:35%;
            margin-left:30%;
            
        }
        table{
          border:1px solid blue;
          width:100%;
          margin:5px;
        }
        td{
          border:1px solid blue;
        }
    </style>
</head>
<body>
    <img src="RGUKT.jpeg" style="float:left;width:70px;height:70px;margin-top:-15px">
    <h4 style="text-align:center;color:green;text-shadow:0px 5px 0px lightgray">RAJIV GHANDI UNIVERSITY OF KNOWLEDGE TECHNOLOGIES::ANDHRA PRADESH<br>E2 SEM-1 EXAMINATION,FEBRUARY-2023</h4>
    <hr>

    <div class="text">
        <h4>MARKS MEMO</h4>
        <form action="<?php echo $_SERVER['PHP_SELF'];?>"method="post">
            <label for="roll no">ROLL NUMBER:</label>
            <input type="text"id="rollno"name="rollno" placeholder="O190xxx" required>
            <div class="button">
                <input type="submit" value="submit">
                <button>print</button>
            </div>
        </form>
    </div>
    

    <table>
    <?php
    $rollno=$_POST['rollno'];
    $con=mysqli_connect("localhost","root","","students")or die("unable to connect");
    $sql="select *from student where rollno='$rollno'";
    $result=mysqli_query($con,$sql);
    while($row=mysqli_fetch_row($result))
    {
    ?>
        <tr>
          <td>ROLL NUMBER</td>
          <td colspan="2"><?php echo $row[0]; ?></td>
        </tr>
        <tr>
          <td>CANDIDATES NAME</td>
          <td colspan="2"><?php echo $row[1];?></td>
        </tr>
        <tr>
          <td>FATHER NAME</td>
          <td colspan="2"><?php echo $row[2];?></td>
        </tr>
        <tr>
          <td><b>SUBJECT</b></td>
          <td><b>SECURED MARKS</b></td>
          <td><b>RESULTS</b></td>
        </tr>
        <tr>
          <td>P&S</td>
          <td><?php echo $row[5];?></td>
          <td><?php echo $row[9];?></td>
        </tr>
        <tr>
          <td>DAA</td>
          <td><?php echo $row[4];?></td>
          <td><?php echo $row[9];?></td>
        </tr>
        <tr>
          <td>DBMS</td>
          <td><?php echo $row[6];?></td>
          <td><?php echo $row[9];?></td>
        </tr>
        <tr>
          <td>DLD</td>
          <td><?php echo $row[5];?></td>
          <td><?php echo $row[9];?></td>
        </tr>
        <tr>
          <td>FLAT</td>
          <td><?php echo $row[3];?></td>
          <td><?php echo $row[9];?></td>
        </tr>
        <tr>
          <td colspan="3">GRAND TOTAL:<?php echo $row[8];?></td>
        </tr>
        <tr>
          <td colspan="3">RESULT:<?php if($row[8]>450){echo "FIRST DIVISION";} 
                                        elseif($row[8]>300){echo "SECOND DIVISION";}
                                        elseif($row[8]>155){echo "THIRD DIVISION";}
                                        else {echo "REMIDIAL";}?>
          </td>
        </tr>
    <?php
    }
     ?>   
    </table>
</body>
</html>
