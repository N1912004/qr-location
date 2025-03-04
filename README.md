<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yêu cầu vị trí</title>
    <script>
        function requestLocationAndSubmit() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    showPosition,
                    showError,
                    { enableHighAccuracy: true, timeout: 10000, maximumAge: 0 }
                );
            } else {
                alert("Trình duyệt không hỗ trợ định vị!");
            }
        }

        function showPosition(position) {
            var latitude = position.coords.latitude;
            var longitude = position.coords.longitude;

            // Đường dẫn Google Forms (thay đúng ID của form bạn)
            var formURL = "https://docs.google.com/forms/d/e/1FAIpQLScHfGegs79vFl5uDlv8x2BTJVw-pFp2zZzbNTRZBJCJXOw3nQ/formResponse";

            // Thêm dữ liệu vị trí vào URL
            var fullURL = formURL + "?entry.1233543830=" + encodeURIComponent(latitude + "," + longitude);

            // Gửi dữ liệu lên Google Forms
            fetch(fullURL, { method: "POST", mode: "no-cors" })
                .then(() => {
                    alert("Vị trí đã được lưu! Đang mở Google Forms...");
                    window.location.href = "https://docs.google.com/forms/d/e/1FAIpQLScHfGegs79vFl5uDlv8x2BTJVw-pFp2zZzbNTRZBJCJXOw3nQ/viewform";
                })
                .catch((error) => {
                    alert("Lỗi khi gửi dữ liệu: " + error);
                });
        }

        function showError(error) {
            switch (error.code) {
                case error.PERMISSION_DENIED:
                    alert("Người dùng từ chối cấp quyền vị trí!");
                    break;
                case error.POSITION_UNAVAILABLE:
                    alert("Thông tin vị trí không khả dụng!");
                    break;
                case error.TIMEOUT:
                    alert("Hết thời gian yêu cầu vị trí!");
                    break;
                case error.UNKNOWN_ERROR:
                    alert("Lỗi không xác định!");
                    break;
            }
        }
    </script>
</head>
<body onload="requestLocationAndSubmit()">
    <h2>Đang yêu cầu vị trí...</h2>
</body>
</html>
