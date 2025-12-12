<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>



    <p id="city"></p>
    <p id="weather"></p>
    <p id="Temp"></p>
    <script>

       // 直接將網址字串放入 fetch 中
fetch("https://nutc-web-vic-peng.zeabur.app/api/weather/kaohsiung")
  .then(response => {
    // 步驟 1: 收到回應，轉成 JSON
    return response.json();
  })
  .then(result => {
    // 步驟 2: 成功拿到 JSON 資料 (result)
    console.log("成功取得資料！", result);

    // 根據 API 結構，天氣資料放在 result.data 裡面
    const weatherInfo = result.data;

    // 印出我們感興趣的欄位
    console.log("城市：", weatherInfo.city);
    console.log("目前天氣：", weatherInfo.forecasts[0].weather);
    console.log("氣溫範圍：", weatherInfo.forecasts[0].minTemp + " ~ " + weatherInfo.forecasts[0].maxTemp);
    document.getElementById('city').innerText=weatherInfo.city ;
    document.getElementById('weather').innerText=weatherInfo.forecasts[0].weather;
    document.getElementById('Temp').innerText=weatherInfo.forecasts[0].minTemp + " ~ " + weatherInfo.forecasts[0].maxTemp;
    })



  .catch(error => {
    // 步驟 3: 如果發生錯誤 (如網址打錯、網路不通)
    console.error("發生錯誤：", error);
  });

    </script>




</body>
</html>
