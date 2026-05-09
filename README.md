# LaptrinhROS
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
