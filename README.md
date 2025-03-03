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

    // URL của Google Forms (thay đúng ID của bạn)
    var formURL = "https://docs.google.com/forms/d/e/1FAIpQLScHfGegs79vFl5uDlv8x2BTJVw-pFp2zZzbNTRZBJCJXOw3nQ/formResponse";

    // Dữ liệu gửi lên form (Thay đúng `entry.xxx` của bạn)
    var formData = new FormData();
    formData.append("entry.6288103361519107001", latitude + "," + longitude);

    // Gửi dữ liệu lên Google Forms
    fetch(formURL, {
        method: "POST",
        body: formData,
        mode: "no-cors"  // Quan trọng: Bỏ lỗi CORS
    }).then(() => {
        alert("Vị trí đã được lưu thành công!");
    }).catch((error) => {
        alert("Lỗi khi gửi dữ liệu: " + error);
    });
}

// Kiểm tra trình duyệt có hỗ trợ định vị không
if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
} else {
    alert("Trình duyệt của bạn không hỗ trợ định vị!");
}

// Kiểm tra xem trình duyệt có hỗ trợ Geolocation không
if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
} else {
    alert("Trình duyệt của bạn không hỗ trợ định vị!");
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

