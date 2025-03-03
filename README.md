<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>QR Location Tracker</title>
    <script>
    
var entryMSSV = "367227771"; // Thay bằng entry của MSSV
var entryHoTen = "1285619517"; // Thay bằng entry của Họ và tên
var entryDiaChi = "300113824"; // Thay bằng entry của Địa chỉ

function showPosition(position) {
    var latitude = position.coords.latitude;
    var longitude = position.coords.longitude;
    var mssv = prompt("Nhập MSSV:");
    var hoTen = prompt("Nhập Họ và Tên:");
    var diaChi = latitude + "," + longitude; // Dùng vị trí làm địa chỉ

    // URL Google Forms
    var formURL = "https://docs.google.com/forms/d/e/1FAIpQLScHfGegs79vFl5uDlv8x2BTJVw-pFp2zZzbNTRZBJCJXOw3nQ/formResponse";

    // Tạo URL gửi dữ liệu
    var fullURL =
        formURL +
        "?entry." + entryMSSV + "=" + encodeURIComponent(mssv) +
        "&entry." + entryHoTen + "=" + encodeURIComponent(hoTen) +
        "&entry." + entryDiaChi + "=" + encodeURIComponent(diaChi);

    // Gửi dữ liệu tự động
    fetch(fullURL, { method: "POST", mode: "no-cors" })
        .then(() => {
            alert("Dữ liệu đã lưu! Kiểm tra Google Forms.");
        })
        .catch((error) => {
            alert("Lỗi gửi dữ liệu: " + error);
        });
}

// Kiểm tra và lấy vị trí
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

