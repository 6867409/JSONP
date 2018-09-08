# JSONP
封装JSONP
document.onclick = function(){
			var url = "http://127.0.0.1/1807/ajax/data/jsonp-fn.php"
			jsonp(url,function(res){
				console.log(res)
			},{
				user:"shanghai",
				cb:"abcadas",
				_fnName:"cb"
			})
		}
		
		function jsonp(url,callback,data){
			var str = ""
			for(var i in data){
				str = str + i + "=" + data[i] + "&";
			}
			
			url = url + "?" + str.slice(0,str.length-1);
			
			var script = document.createElement("script")
			script.src = url;
			document.body.appendChild(script);
			
			window[data[data._fnName]] = function(res){
				callback(res)
			}
		}
		
