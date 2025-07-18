# XXYSHSH
查询身份证后六位序号工具
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <title>查询序号</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 30px; }
    input, button { font-size: 18px; padding: 8px; margin-top: 10px; }
    #result { margin-top: 20px; font-size: 20px; color: #333; }
  </style>
</head>
<body>
  <h2>请输入您的姓名或身份证后六位进行查询：</h2>
  <input type="text" id="inputValue" placeholder="姓名或身份证后六位">
  <button onclick="search()">查询</button>
  <div id="result"></div>

  <script src="data.js"></script>
  <script>
    function search() {
      const input = document.getElementById("inputValue").value.trim();
      const matches = data.filter(p => p.name === input || p.last6 === input);
      const resultDiv = document.getElementById("result");

      if (matches.length > 0) {
        resultDiv.innerHTML = matches.map(match => `
          查询成功！<br>
          姓名：<strong>${match.name}</strong><br>
          报名场次：<strong>${match.session}</strong><br>
          序号：<strong>${match.index}</strong>
        `).join('<hr>');
      } else {
        resultDiv.innerHTML = "未找到匹配的信息，请检查输入是否正确。";
      }
    }
  </script>
</body>
</html>
