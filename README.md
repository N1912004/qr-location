<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>QR Location Tracker</title>
    <script>
    
function showPosition(position) {
    var latitude = position.coords.latitude;
    var longitude = position.coords.longitude;

    // URL Google Forms (thay đúng ID của bạn)
    var formURL = "https://docs.google.com/forms/d/e/1FAIpQLScHfGegs79vFl5uDlv8x2BTJVw-pFp2zZzbNTRZBJCJXOw3nQ/viewform";

    // Thêm vị trí vào URL (thay đúng `entry.xxx`)
    var fullURL = formURL + "?entry.YPqjbf=" + latitude + "," + longitude;

    // Mở form với tọa độ đã điền sẵn
    window.location.href = fullURL;
}

// Kiểm tra trình duyệt có hỗ trợ GPS không
if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
} else {
    alert("Trình duyệt không hỗ trợ định vị!");
}





        function showError(error) {
            switch (error.code) {
                case error.PERMISSION_DENIED:
                    alert("Bạn đã từ chối truy cập vị trí.");
                    break;
                case error.POSITION_UNAVAILABLE:
                    alert("Không thể xác định vị trí.");
                    break;
                case error.TIMEOUT:
                    alert("Quá thời gian yêu cầu vị trí.");
                    break;
                default:
                    alert("Lỗi không xác định.");
            }
        }
    </script>
</head>
<body onload="getLocation()">
    <h2>Đang lấy vị trí...</h2>
    <p id="location"></p>
</body>
</html>

