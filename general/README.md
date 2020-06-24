# Cấu trúc của một Dự Án theo mô hình MVP

#### Base Application
* data
	* remote
	* local
	* model
* presenter
* service
* ui
  * activity
  * adapter
  * customview
  * dialog
  * fragment
  * widget
* util

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
| Action bar    | `ab_`         | `ab_stacked`          |
| Button        | `btn_`	      | `btn_next`            |
| Dialog        | `dialog_`     | `dialog_rating`       | 
| EditText      | `edit_`       | `edit_password`       |
| FrameLayout  | `frame_`	    | `frame_container`         |
| ImageView     | `image_`	    | `image_star`          |
| LinearLayout  | `linear_`	    | `linear_container`         |
| ListView      | `lview_`	    | `lview_users`         |
| Menu          | `menu_	`     | `menu_settings`       |
| RecyclerView  | `rview_`	    | `rview_fonts`         |
| RelativeLayout  | `relative_`	    | `relative_container`         |
| SearchView    | `sview_`	    | `sview_song`         |
| TextView      | `text_`       | `text_user_name`      |
| VideoView     | `vview_`      | `vview_guide`         |
| WebView       | `wview_`      | `wview_home`          |

Quy ước đặt tên cho Icon :

| Kiểu                            | Tiếp tố            | Ví dụ                        |
| --------------------------------| ----------------   | ---------------------------- | 
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

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
| Partial layout   | ---                    | `layout_partial_stats_bar.xml`       |

#### 1.2.3 Menu files

Vì menu không chứa các thành phần Android nên để đặt tên Menu cần nên đặt tên theo màn hình sử dụng. Ví dụ trong `MainActivity` thì tên file menu sẽ là `activity_main.xml`

Chú ý rằng tên file không cần bao gồm `menu` vì file đã được chứa trong thư mục `menu`

#### 1.2.4 Values files

Tên tập tin nên có thêm __số nhiều__. Ví dụ `strings.xml`, `styles.xml`, `colors.xml`, `dimens.xml`, `attrs.xml`
