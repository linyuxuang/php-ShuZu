# php-ShuZu
php数组基础
 一、数组的概述
  	1. 数组的本质：管理和操作一组变量，成批处理
 	2. 数组是复合类型
  	3. 数组中可以存储任意长度的数据，也可以存储任意类型的数据
       4. 数组就可以完成其它语言数据结构的功能（链表， 队列， 栈， 集合类）
       
  二、数组的分类
      数组中存有多个单元，（单元称为元素）
      每个元素（下标［键］和值）
      单访问元素时候，都是通过下标（键）来访问元素
 
  	1. 一维数组， 二维数组， 三维数组 。。。 多维数组
 	（数组的数组， 就是在数组中存有其它的数组）
 	2. PHP中有两种数组
 	索引数组：就是下标是顺序整数作为索引  
 	关联数组：就是下标是字符串作为索引
 
 	下标（整数， 字符串）只有这两种
 
 三、数组多种声明方式
 
      1. 直接为数组元素赋值
      	   a.如果索引下标不给出，就会从0开始顺序索引
 	   b.如果给出索引下标，下一个就会是从最大的开始增1
 	   c.如果后面出现前面的下标，如果是赋值就是为前面的元素重新赋值
           
           d. 混合声明时，索引和关联不互相影响(不影响索引下标的声明)
     2. 使用array()函数
     	  a. 默认是索引数组
      	  b.如果为关联数组和索引数组指定下标，使用 键=>值
      3. 使用其它的函数声明
         file();
 
 
     
  例子1
	
                          $user["id"]=1;
                          $user["name"]="zhangsan";
                          $user["age"]=10;
                          $user["sex"]="nan";
                          $user["email"]="aaa@bb.com";

                          echo '<pre>';
                          print_r($user);
                          echo '</pre>';
                          $user["age"]=90;
                          echo $user["age"];


 例子2

                       $user=array(1, "zhsangsan", 10, "nan", "aaa@bbb.com");

                          echo '<pre>';
                          print_r($user);
                          echo '</pre>';


例子3
 
 
                          $info=array(
                            "user"=>array(
                                //$user[0]
                                array(1, "zansan", 10, "nan"),
                                //$user[1][1]
                                array(2, "lisi", 20, "nv"),    //$user[1]
                                //$user[2]
                                array(3, "wangwu", 30, "nan")
                            ),
                            "score"=>array(
                                array(1, 100, 90, 80),
                                array(2, 99, 88, 11),
                                array(3, 10, 50, 88)
                              ),
                            "connect"=>array(
                                array(1, '110', 'aaa@bbb.com'),
                                array(2, '120', 'bbb@ccc.com'),
                                array(3, '119', 'ccc@ddd.com')	
                              )
                          );

                        echo $info["connect"][1][2];

                              echo '<pre>';
                              print_r($info);
                              echo '</pre>';



例子4




                              $user[0][]=1;
                              $user[0][]=1;
                              $user[0][]=1;
                              $user[1][]=1;
                              $user[1][]=1;
                              $user[][]=1;
                              $user[][]=1;

                              echo '<pre>';
                              print_r($user);
                              echo '</pre>';


  数组的遍历
 
 	1. 使用for语句循环遍历数组
  	   a. 其它语言（只有这一种方式）
           b. PHP中这种方式不是我们首选方式
           c. 数组必须是索引数组，而且下标还必须是连续的
            （索引数组下标还可以不连序，数组还有关联数组）
    
 
  	2. 使用foreach语句循环遍历数组
  	   foreach(数组变量 as 变量值){
 		//循环体
  	   }
 	   a. 循环次数由数组的元素个数决定
  	   b. 每一次循环都会将数组中的元素分别赋值给后面变量
 
  	   foreach(数组变量 as 下标变量=> 值变量){
 		
  	   }
 
  	3. while() list() each() 组合循环遍历数组
 
        each()函数， 
        	a. 需要一个数组作为参数
        	b. 返回来的也是一个数组
        	c. 返回来的数组是0, 1, key, value四个下标(固定的)
        	 0和key下标是当前参数数组元素的鍵
        	 1和value下标是当前对数数组元素的值
 
               d. 默认认当前元素就是第一个元素
               e. 每执行一次后就会将当前元素向后移动
               f. 如果到最后的元素再执行这个函数，则返回false
 
 *		//Array ( [1] => 1 [value] => 1 [0] => id [key] => id ) 
 *    
 *      list()函数
 
 * 		a. list()=array(); 需要将一个数组赋值给这个函数
 * 		b. 数组中的元素个数，要和list()函数中的参数个数相同
 * 		c. 数组中的每个元素值会赋值list()函数中的每个参数，list()将每个参数转为变量
 
 
 
    for循环 （php里面不推荐使用）
 
 
                    $user=array(1, "zhasna", 40, "nan", "aaa@bb.com");
  
	             for($i=0; $i<count($user); $i++){
		     echo "\$user[{$i}]=".$user[$i]."<br>";
	         }

foreach（php里面推荐使用）
 
			  $user=array(1, "name"=>"zhasna", "age"=>40, 100=>"nan", "aaa@bb.com");

			  foreach($user as $key=>$val){   //$var 是自定义变量, $key自定义变量
					echo $key."=========>".$val."<br>";
			  }
			  
			  
			  
 例子  foreach
                 
		    $info=array(
		"user"=>array(
				//$user[0]
				array(1, "zansan", 10, "nan"),
				//$user[1][1]
				array(2, "lisi", 20, "nv"),    //$user[1]
				//$user[2]
				array(3, "wangwu", 30, "nan")
		),
		"score"=>array(
				array(1, 100, 90, 80),
				array(2, 99, 88, 11),
				array(3, 10, 50, 88)
			),
		"connect"=>array(
				array(1, '110', 'aaa@bbb.com'),
				array(2, '120', 'bbb@ccc.com'),
				array(3, '119', 'ccc@ddd.com')	
			)
		);

		foreach($info as $tableName=>$table){
			echo '<table align="center" width="500" border="1">';
			echo '<caption><h1>'.$tableName.'</h1></caption>';
			foreach($table as $row){
				echo '<tr>';
				foreach($row as $col){
					echo '<td>'.$col.'</td>';
				}
				echo '</tr>';
			}
			echo '</table>';
		}
 
 each()
 
               $user=array("id"=>1, "name"=>"zhangsan", "age"=>10, "sex"=>"nan");
	
	      while($arr=each($user)){
		//echo $arr[0]."==>".$arr[1]."<br>";
	 	 echo $arr["key"]."---->".$arr["value"]."<br>";
	  }
	  
	  
	  
list()	  
			  
		list($name, $age, $sex)=array("zansan", 10, "nnnnn");

			echo $name."<br>";
			echo $age."<br>";
			echo $sex."<br>";	  

list例子



      $ip="192.168.1.128";

	list(, , , $d)=explode(".", $ip);

	echo $d;
	
	
	
each和list配合	
	
	
	$user=array("id"=>1, "name"=>"zhangsan", "age"=>10, "sex"=>"nan");

	list($key, $value)=each($user);  //Array ( [1] => 1  [0] => id  ) 

	echo $key."-->".$value;
