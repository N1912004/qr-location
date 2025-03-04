function showPosition(position) {
    var latitude = position.coords.latitude;
    var longitude = position.coords.longitude;

    // URL Google Forms (chỉnh sửa đúng link của bạn)
    var formURL = "https://docs.google.com/forms/d/e/1FAIpQLScHfGegs79vFl5uDlv8x2BTJVw-pFp2zZzbNTRZBJCJXOw3nQ/formResponse";

    // Dữ liệu gửi lên Google Forms (thay đúng `entry.xxx`)
    var fullURL = formURL + "?entry.6288103361519107001=" + latitude + "," + longitude;

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

// Kiểm tra trình duyệt có hỗ trợ GPS không
if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(showPosition);
} else {
    alert("Trình duyệt không hỗ trợ định vị!");
}
