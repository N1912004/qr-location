function showPosition(position) {
    var latitude = position.coords.latitude;
    var longitude = position.coords.longitude;

    // URL Google Forms (thay đúng ID của bạn)
    var formURL = "https://docs.google.com/forms/d/e/1FAIpQLScHfGegs79vFl5uDlv8x2BTJVw-pFp2zZzbNTRZBJCJXOw3nQ/viewform";

    // Thêm vị trí vào URL (thay đúng `entry.xxx`)
    var fullURL = formURL + "?entry.6288103361519107001=" + latitude + "," + longitude;

    // Mở form với tọa độ đã điền sẵn
    window.location.href = fullURL;
}

// Kiểm tra trình duyệt có hỗ trợ GPS không
if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
} else {
    alert("Trình duyệt không hỗ trợ định vị!");
}
