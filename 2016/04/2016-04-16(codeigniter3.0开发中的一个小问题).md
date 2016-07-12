# codeigniter3.0开发中的一个小问题  #

今天把一个codeigniter程序部署到linux(centos)下的nginx的时候出现了
**Unable to locate the model you have specified:*_model**  这个问题.

顺手粘贴到网上搜索了一下，这是由于大小写问题引起的。

在codeigniter3.0中，model文件名的首字母必须大写，如 `User_model.php`，在这个文件中，书写规则如下：

```
// 注意这里的'User_model'
class User_model extends CI_Model{
        //验证用户是否已经登陆
        public function adminValid(){
            $user = $this->session->userdata('user_name');  
            if (empty($user)) {
                $url = site_url('login/index');
                echo "<script>window.location='$url';</script>";
            }
        }
    }
```

在`controller`中，使用如下： 

```
public function __construct(){
    parent::__construct(); //调用父类的构造方法
    // header("Content-Type:text/html;charset=utf-8");
    error_reporting(E_ALL ^E_NOTICE);
    //登陆验证...
    $this->load->model('user_model','user');
    $this->user->adminValid();
    //权限验证...
}
```

这个规则是必须遵守的，在Windows下无所谓，但是在Linux下就会出问题。