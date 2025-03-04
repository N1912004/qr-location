<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Google Form với GPS</title>
    <script>
        function getGPS() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(function(position) {
                    let latitude = position.coords.latitude;
                    let longitude = position.coords.longitude;
                    let gpsData = latitude + ", " + longitude;
                    
                    // Chuyển hướng đến URL của Google Form với dữ liệu GPS
                    let formURL = "https://docs.google.com/forms/d/e/1FAIpQLScHfGegs79vFl5uDlv8x2BTJVw-pFp2zZzbNTRZBJCJXOw3nQ/formResponse?entry.6288103361519107001=" + encodeURIComponent(gpsData);
                    window.location.href = formURL;
                }, function(error) {
                    alert("Không thể lấy vị trí! Hãy bật GPS trên thiết bị.");
                });
            } else {
                alert("Trình duyệt của bạn không hỗ trợ GPS.");
            }
        }
        
        // Đợi trang tải xong rồi lấy vị trí
        window.onload = function() {
            setTimeout(getGPS, 1000);
        };
    </script>
</head>
<body>
    <h2>Đang lấy vị trí GPS, vui lòng đợi...</h2>
</body>
</html>
