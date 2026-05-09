🤖 Mô Phỏng Robot Di Động ROS 2 (myrobot)

Một package mô phỏng ROS 2 dành cho hệ thống robot di động tùy chỉnh. Dự án này thể hiện cách thiết lập mô hình vật lý cơ bản cho robot (sử dụng URDF/Xacro), cách tích hợp các loại cảm biến và chạy mô phỏng môi trường thông qua Gazebo và RViz.
🚀 Tính năng nổi bật

    Truyền động Vi sai (Differential/Skid-Steer Drive): Cấu hình động học di chuyển tùy chỉnh.

    Tích hợp Cảm biến:

        📷 Camera: Phục vụ các tác vụ xử lý hình ảnh và thị giác máy tính.

        📡 LiDAR (2D): Ứng dụng cho việc tránh vật cản, vẽ bản đồ và chạy thuật toán SLAM.

        🧭 IMU: Đo gia tốc tuyến tính và vận tốc góc của hệ thống.

    Môi trường Mô phỏng: Hỗ trợ đầy đủ hiển thị trực quan dữ liệu trên Gazebo và RViz.

🛠️ Yêu cầu hệ thống (Prerequisites)

    Ubuntu 22.04

    ROS 2 Humble

    Gazebo

📦 Cài đặt

Trước khi khởi chạy hệ thống mô phỏng, bạn cần cài đặt package teleop để có thể điều khiển robot di chuyển bằng bàn phím.

Mở terminal và chạy lệnh sau:
Bash

# Cài đặt package teleop_twist_keyboard
sudo apt install ros-$ROS_DISTRO-teleop-twist-keyboard

# Hoặc lệnh cài trực tiếp cho bản Humble:
# sudo apt install ros-humble-teleop-twist-keyboard

🎮 Hướng dẫn Khởi chạy & Sử dụng

Để chạy toàn bộ hệ thống mô phỏng, bạn sẽ cần mở nhiều tab terminal khác nhau. Hãy đảm bảo bạn đang đứng ở thư mục gốc của ROS 2 workspace (ví dụ: ~/ros2_ws) trước khi chạy các lệnh dưới đây.
1. Khởi chạy Môi trường Gazebo

Ở terminal đầu tiên, source workspace và khởi chạy môi trường vật lý Gazebo:
Bash

source install/setup.bash
ros2 launch myrobot gazebo.launch.py

2. Khởi chạy Hiển thị trực quan RViz

Mở terminal thứ hai để chạy RViz. Đây là nơi bạn quan sát mô hình 3D của robot, kiểm tra cây tọa độ TF, và theo dõi trực tiếp dữ liệu cảm biến (PointCloud/LaserScan):
Bash

source install/setup.bash
ros2 launch myrobot display.launch.py

3. Điều khiển Robot

Mở terminal thứ ba để chạy node điều khiển. Bạn có thể sử dụng các phím trên bàn phím để lái robot di chuyển xung quanh căn phòng mô phỏng:
Bash

ros2 run teleop_twist_keyboard teleop_twist_keyboard

4. Kiểm tra Dữ liệu Cảm biến

Bạn có thể mở thêm terminal để kiểm tra xem các cảm biến có đang hoạt động và publish dữ liệu chính xác hay không:

Kiểm tra dữ liệu IMU:
Bash

ros2 topic echo /imu/data

Xem luồng hình ảnh từ Camera:
Bash

ros2 run rqt_image_view rqt_image_view

(Lưu ý: Chọn topic /camera/image_raw từ menu thả xuống trong cửa sổ giao diện RQT).
