1. $.AJAX中如果是GET方法，那么data在req.query里;如果是POST方法，data在req.body里(req.body.action, req.body.data)

var reqData = {};
reqData.action = "update";
reqData.data = data;

$.ajax({
      type: "POST",
      url: "/api",
      data: reqData ,
      //contentType:"application/json"
      error: function(jqXHR, textStatus, errorThrown){
        if (jqXHR.status == 400) {
          alert(jqXHR.responseText);
        } else {
          console.log(jqXHR);
          alert("未知错误！");
          //alert(jqXHR.responseText);
        }
      }
  });
  
  2. jquery里控件id带特殊字符里需要转义(特殊字符前加\\) 如id = abc-cd(aa)
  直接用$("#"+id)就会出错，需要把id转换成abc-cd\\(aa\\)才可以
  或者用$("[value='" + id + "']")
