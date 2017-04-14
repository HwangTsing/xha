//查看全榜
$(function(){
	mui(".left_hot").on('tap','a',function(){
		window.location.href="ratings.html";
	})
	mui(".center_hot").on('tap','a',function(){
		window.location.href="tv_week.html";
	})
	mui(".right_hot").on('tap','a',function(){
		window.location.href="tv_week02.html";
	})
	/*mui(".bg_box").on('tap','a',function(){
		window.history.go(-1);
	})
	*/
	function getList(type,cb){
		var url = serverUrl + "mob/getMobWeekTop.do";
		mui.ajax(url, {
			type: 'post',
			dataType: "json",
			data: {
				typecode: type,
				pagenum: 3
			},
			headers: {
				'Content-Type': 'application/x-www-form-urlencoded'
			},
			success: function(data){
				//console.log(data);
				if (data.success) {
					$("#dsj tbody").html(str);
					var str = "";
					for(var i = 0 ; i <data.data.length; i ++){
						if(i<3){
							str += "<tr><td>"+ (i+1)+"."+data.data[i].name.substring(0,8) +"</td><td>"+data.data[i].num+"次</td></tr>";
						}
						
					}
					if(type == 1){//电视剧
						$("#dsj tbody").html(str);
					}else if(type == 2){//电影
						$(".ranking_time01").html(d.getDateStr(-8) +"---"+d.getDateStr(-1));
						$("#dy tbody").html(str);
					}else if(type == 4){//综艺
						$(".time_wz").html(d.getDateStr(-8) +"---"+d.getDateStr(-1));
						$("#zy tbody").html(str);
					}
					
				}
				else {
				//alert("获取数据失败");
				}
			},
			error: function(){
			// alert("数据读取错误!");
			}
		});
	}
	function init(){
		$(".ranking_time").html(d.getDateStr(-8) +"---"+d.getDateStr(-1));
		$(".date").html(d.getDateStr(-8) +"---"+d.getDateStr(-1));
		getList(1);
		getList(2);
		getList(4);
	}
	init();
	
	var imgSrc = "images/week01.png",imgSrc02 = "images/week02.png",imgSrc03 = "images/week03.png";//本地项目文件夹下的图片
	function getBase(img){//传入图片路径，返回base64
		function getBase64Image(img,width,height) {
	          var canvas = document.createElement("canvas");
	          canvas.width = width ? width : img.width;
	          canvas.height = height ? height : img.height;
	          var ctx = canvas.getContext("2d");
	          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
	          var dataURL = canvas.toDataURL();
	          return dataURL;
        }
        var image = new Image();
        image.src = img;
        var deferred=$.Deferred();
        if(img){
	          image.onload =function (){
	            deferred.resolve(getBase64Image(image));//将base64传给done上传处理
	          }
          	return deferred.promise();//问题要让onload完成后再return sessionStorage['imgTest']
        }
      }
      getBase(imgSrc)
        .then(function(base64){
          //console.log(base64);
        },function(err){
          //console.log(err);
        });
        
        
        
   	function getBase64(img){//传入图片路径，返回base64
		function getBase64Im(img,width,height) {
	          var canvas = document.createElement("canvas");
	          canvas.width = width ? width : img.width;
	          canvas.height = height ? height : img.height;
	          var ctx = canvas.getContext("2d");
	          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
	          var dataURL = canvas.toDataURL();
	          return dataURL;
        }
        var image = new Image();
        image.src = img;
        var deferred=$.Deferred();
        if(img){
	          image.onload =function (){
	            deferred.resolve(getBase64Im(image));//将base64传给done上传处理
	          }
          	return deferred.promise();//问题要让onload完成后再return sessionStorage['imgTest']
        }
      }
      getBase64(imgSrc02)
        .then(function(base64){
          //console.log(base64);
        },function(err){
          //console.log(err);
        });
        
        
         
   	function getBase64img(img){//传入图片路径，返回base64
		function getBase64Im03(img,width,height) {
	          var canvas = document.createElement("canvas");
	          canvas.width = width ? width : img.width;
	          canvas.height = height ? height : img.height;
	          var ctx = canvas.getContext("2d");
	          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
	          var dataURL = canvas.toDataURL();
	          return dataURL;
        }
        var image = new Image();
        image.src = img;
        var deferred=$.Deferred();
        if(img){
	          image.onload =function (){
	            deferred.resolve(getBase64Im03(image));//将base64传给done上传处理
	          }
          	return deferred.promise();//问题要让onload完成后再return sessionStorage['imgTest']
        }
      }
    getBase64img(imgSrc03)
        .then(function(base64){
          //console.log(base64);
        },function(err){
          //console.log(err);
        });
	
})
