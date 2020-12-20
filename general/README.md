# Cấu trúc của một Dự Án theo mô hình MVVM

#### Base Application
* data
  * remote
  * local
  * model
  * repo
* helper
  * di (Dagger injection)
  * rx (Rxjava, RxKotlin, RxAndroid)
  * sharedpref (Shared Preferences)
  * admob
  * firebase
* service
* view
  * base
  * activity
  * adapter
  * custom
  * dialog
  * fragment
* util (BindingUtils, Enums, Constants, Extensions)
* MainApplication

## 1. Cách đặt tên files

### 1.1 Class files

Tên class phải được viết theo kiểu [UpperCamelCase](https://en.wikipedia.org/wiki/CamelCase)

Đối với những lớp mở rộng trong Android thì tên của class nên kết thúc bằng tên của lớp mở rộng đó

Ví dụ: MainActivity, LoginFragment, UserController, WeatherService, SignInDialog....

### 1.2 Tên file tài nguyên <Resources>

Được đặt theo định dạng : `lowercase_underscore`

Ví dụ: activity_main, fragment_login, dialog_sign_in,...

#### 1.2.1 Tên file Drawables

Quy ước đặt tên cho Id:
Tên ID nên được bắt đầu bằng tiền tố là tên phần tử, tất cả chữ thường và gạch chân


| Kiểu          | Tiền tố       |		Ví dụ               |
|---------------| --------------|-----------------------|
| Tool bar    | `tool_bar`         | `tool_bar_main`          |
| Button        | `button_`	      | `button_next`            |
| ConstraintLayout  | `constraint_`	    | `constraint_container`         |
| Dialog        | `dialog_`     | `dialog_rating`       | 
| EditText      | `edit_`       | `edit_password`       |
| FrameLayout  | `frame_`	    | `frame_container`         |
| ImageView     | `image_`	    | `image_star`          |
| LinearLayout  | `linear_`	    | `linear_container`         |
| ListView      | `list_`	    | `list_users`         |
| Navigation bar          | `navigation_	`     | `navigation_home`       |
| RecyclerView  | `rview_`	    | `rview_fonts`         |
| RelativeLayout  | `relative_`	    | `relative_container`         |
| View    | `view_`	    | `view_background`         |
| TextView      | `text_`       | `text_user_name`      |
| VideoView     | `vview_`      | `vview_guide`         |
| TabLayout       | `tab_layout`      | `tab_layout_home`          |

Quy ước đặt tên cho Icon :

| Kiểu                            | Tiền tố            | Ví dụ                        |
| --------------------------------| ----------------   | ---------------------------- | 
| Icons                           | `ic_`              | `ic_star.png`                |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |
| Background                      | `bg_dialog`        | `bg_dialog_info.png`         |

Tên cho selector states:

| Trạng thái	 | Hậu tố          | Ví dụ                       |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |


#### 1.2.2 Tên Layout

Áp dụng cấu trúc Type _object _ purpose. Tên file phải chứa tên thành phần Android, và nó đặt đầu tiên của tên Files. Ví dụ Tên file layout của `LoginActivity` sẽ là `activity_login.xml`

| Thành phần       | Tên lớp                | Tên layout                    |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Layout khác      | ---                    | `layout_partial_stats_bar.xml`|

#### 1.2.3 Menu files

Vì menu không chứa các thành phần Android nên để đặt tên Menu cần nên đặt tên theo màn hình sử dụng. Ví dụ trong `MainActivity` thì tên file menu sẽ là `activity_main.xml`

Chú ý rằng tên file không cần bao gồm `menu` vì file đã được chứa trong thư mục `menu`

#### 1.2.4 Values files

Tên tập tin nên có thêm __số nhiều__. Ví dụ `strings.xml`, `styles.xml`, `colors.xml`, `dimens.xml`, `attrs.xml`

# Tự tạo một thư viện Android
Một thư viện Android có cấu trúc giống như một mô-đun ứng dụng Android. Nó có thể bao gồm mọi thứ cần thiết để xây dựng một ứng dụng, bao gồm mã nguồn, tệp tài nguyên và Androidmanifest.
Có thể sử dụng thư viện Android trong các trường hợp sau:
* Khi bạn xây dựng nhiều ứng dụng sử dụng một số thành phần giống nhau, chẳng hạn như activities, services, or UI layouts.
* Khi bạn đang xây dựng một ứng dụng tồn tại trong nhiều biến thể APK, chẳng hạn như phiên bản miễn phí và trả phí và bạn cần các thành phần cốt lõi giống nhau trong cả hai.

## Các bước tạo một thư viện Android
### 1. Tạo app module
1. Click File > New > New Module.
2. Giao diện Create New Module xuất hiện, click Android Library > Next.
3. Đặt tên cho module, lựa chọn minSDK và bấm Finish
4. Sau khi hoàn thành Gradle project sync, cấu trúc module xuất hiện như một project
### 2. Chuyển đổi app module thành library module
1. Mở `build.gradle` của module.
2. Xóa thuộc tính `applicationId`
3. Thay đổi
```
apply plugin: 'com.android.application'
```
thành
```
apply plugin: 'com.android.library'
```
4. Click **File > Sync Project with Gradle Files.**
### 3. Sử dụng thư viện
1. Thêm thư viện vào `setting.gradle`
```
include ':app', ':my-library-module'
```
2. Thêm dependency trong app `build.gradle`
```
dependencies {
    implementation project(":my-library-module")
}
```
3. Click **Sync Project with Gradle Files.**
