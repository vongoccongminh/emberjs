# Tìm hiểu EmberJS

## 1. Định nghĩa
- Ember.js là một mã nguồn mở JavaScript phía client khuôn khổ cho việc phát triển các ứng dụng web và sử dụng các cấu trúc mô hình MVC (Model-View-Controller).
## 2. Thuận lợi khi sử dụng EmberJS
- Mã nguồn mở. 
- Linh hoạt, có thể tăng hiệu năng của ứng dụng mà không cần phải load lại cả trang. 
- Sử dụng các thư viện tương tự như HTML. 
- Ứng dụng dùng Ember.js có kích cỡ nhỏ hơn dùng các thư viện khác. 
- Các thuộc tính ràng buộc được hỗ trợ đầy đủ, ví dụ khi đã tạo tạo liên kết giữa 2 thuộc tính, 1 cái thay đổi, cái còn lại được update theo thành giá trị mới. 
## 3. Cài đặt môi trường Ember.js
 Có 2 cách để cài đặt cấu hình Ember.js: 
- Tải các thư viện JavaScript. 
- Sử dụng CDN (Content Delivery Network). Trong đó CDN là một hệ thống máy chủ trên toàn cầu (số lượng tùy theo mỗi nhà cung cấp dịch vụ) làm nhiệm vụ lưu bản sao của các nội dung tĩnh bên trong website, sau đó phân tán nó ra nhiều máy chủ khác (được gọi là PoP – Points of Presence) và từ các PoP đó nó sẽ gửi tới cho người dùng khi họ truy cập vào website. Khi một tập tin được phân phối bởi CDN, người dùng truy cập vào nó thì PoP phân phối gần nhất so với người dùng sẽ trả nội dung về cho người dùng xem. 
## 4. Kiến trúc Ember.js
Kiến trúc của Ember.js về cơ bản bao gồm các thành phần: 
- Template 
- Route 
- Model 
- View 
- Controller 

Trong đó: 
- Template: Mô tả các giao diện người dùng của ứng dụng. Ember.js cung cấp thư viện Handlebar template để xây dựng các ứng dụng front-end, giống như HTML thông thường. Có thể trực tiếp nhúng templates vào các thẻ HTML. Mỗi template được hỗ trợ bởi một model, và các template tự động cập nhật nếu các model thay đổi. 
- Route: Một route là một đối tượng mà nó sẽ làm cho template hiển thị thông tin theo model quy định. Các router dịch một URL vào một loạt các template lồng nhau, mỗi template được hỗ trợ bởi một model. Nếu templates hoặc models thay đổi do người dùng thay đổi, Ember tự động cập nhật URL trên thanh URL của trình duyệt. Điều này có nghĩa rằng, vào thời điểm bất kỳ, người dùng có thể chia sẻ các URL của ứng dụng. Khi ai đó nhấp chuột vào liên kết, họ đang xem nội dung tương tự như người chia sẻ đã thấy. 
- Model: Model là một đối tượng được lưu trong persistent state. Template có trách nhiệm hiển thị các mô hình cho người dùng bằng cách biến nó thành HTML. Các model và route được liên kết với nhau bởi vì model thực hiện các route bằng cách đi qua như là đối số mỗi khi route được gọi đến. 
- View: Xử lý sự kiện người dùng và cập nhật DOM. 
- Controller: Controller quản lý logic hiển thị của model và cũng kiểm soát các hoạt động giữa các route, model, và view. Nó lấy model từ route và tạo ra các kết nối giữa các view, model, and template. Ember.js tự động sinh ra controller.


# Cài đặt TaskApp đơn giản

- Cài đặt Ember CLI
Nhập vào command line:
```sh
$ npm install -g ember-cli
```
Lúc này, Ember command đã được cài đặt trong console. Kiểm tra lại bằng cách:
```sh
$ ember -v
```
Ta sẽ nhận được trên màn hình như sau:
```sh
version: 2.12.1
node: 6.10.2
os: win32 x64
```

- Tạo ứng dụng
Khởi tạo ứng dụng mới: 
```sh
$ ember new my_app
```
Chuyển đến đường dẫn của ứng dụng vừa tạo:
```sh
$ cd my_app
```
- Khởi chạy ứng dụng
Ứng dụng cơ bản đã được thiết lập để có thể chạy được trên trình duyệt. Nhập vào terminal:
```sh
$ ember server
```
Mở trình duyệt vào địa chỉ http://localhost:4200 để truy cập. 
![Home](/images/emberwelcome.png)

Sau đó, tắt server và thêm các route vào project.
Tắt server bằng cách ấn tổ hợp Ctrl + c vào terminal.
Thêm route tasks vào project:
```sh
$ ember g route tasks
```
Sau đó, mở lại server và truy cập vào trang http://localhost:4200/tasks sẽ thấy:
![Home2]((/images/taskswelcome.png))

Thêm route new vào trong tasks
```sh
$ ember g route tasks/new
```

- Thêm Bootstrap vào project
Nhập vào terminal:
```sh
$ bower install bootstrap
```
Thêm dòng lệnh vào file ***ember-cli-build.js***
```javascript
app.import('bower_components/bootstrap/dist/css/bootstrap.css')
```
Tạo navigation bar. Thêm vào file ***application.hbs*** các dòng lệnh sau:
```javascript
<nav class="navbar navbar-default">
      <div class="container">
        <div class="navbar-header">
          <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#navbar" aria-expanded="false" aria-controls="navbar">
            <span class="sr-only">Toggle navigation</span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
            <span class="icon-bar"></span>
          </button>
          <a class="navbar-brand" href="#">My App</a>
        </div>
        <div id="navbar" class="collapse navbar-collapse">
          <ul class="nav navbar-nav">
            <li>{{#link-to 'tasks'}}Home{{/link-to}}</li>
            <li>{{#link-to 'tasks.new'}}New{{/link-to}}</li>
          </ul>
        </div>
      </div>
    </nav>

    <div class="container">
      <div class="row">
        <div class="col-md-12">
          {{outlet}}
        </div>
      </div>
    </div>
```

- Tạo form.
Thêm vào file ***new.hbs*** các dòng lệnh sau
```javascript
<form>
  <div class="form-group">
    <label>Title</label>
    {{input type="text" class="form-control" value=title placeholder="Title of task..."}}
  </div>
  <div class="form-group">
    <label>Date</label>
    {{input type="date" class="form-control" value=date}}
  </div>
  <div class="form-group">
    <label>Description</label>
    {{textarea class="form-control" value=description placeholder="Descripton task..."}}
  </div>
  <button {{action 'addTask'}} class="btn btn-primary">Save</button>
</form>
```

- Tạo controller
Nhập vào terminal:
```sh
$ ember g controller tasks
$ ember g controller tasks/new
```

Bắt sự kiện click vào button **save**, ta thêm vào file ***new.js*** trong thư mục *controller/tasks* như sau:
```javascript
  actions: {
    addTask: function(){
      var title = this.get('title');
      var description = this.get('description');
      var date = this.get('date');

      //create new tasks
      var newTask = this.store.createRecord('task', {
        title: title,
        description: description,
        date: new Date(date)
      });

      //save to database
      newTask.save();

      //clear form
      this.setProperties({
        title: '',
        description: '',
        date: ''
      });
    }
  }
```

- Tạo model
Nhập vào terminal
```sh
$ ember g model task
```
Thêm vào file ***task.js***
```javascript
import DS from 'ember-data';

export default DS.Model.extend({
title: DS.attr('string'),
description: DS.attr('string'),
date: DS.attr('date'),
created: DS.attr('string', {
  defaultValue: function(){
    return new Date();
  }
})
});
```

- Cài đặt emberfire
Nhập vào terminal 
```sh
$ ember install emberfire
```

Cài đặt lại biến môi trường trong file ***enviroment.js***:
```javascript
  contentSecurityPolicy: {
      'script-src': "'self' 'unsafe-eval' apis.google.com",
      'frame-src': "'self' https://*.firebaseapp.com",
      'connect-src': "'self' wss://*.firebaseio.com https://*.googleapis.com"
    },
    rootURL: '/',
   
    firebase: {
      apiKey: "AIzaSyDbpN-c8H8KexU4nVrVD9b86Dkikos8P6o",
   authDomain: "myapp-449f5.firebaseapp.com",
   databaseURL: "https://myapp-449f5.firebaseio.com",
   projectId: "myapp-449f5",
   storageBucket: "myapp-449f5.appspot.com",
   messagingSenderId: "891880234199"
 },
```
Lưu ý: những dòng code trên được phát sinh khi tạo project để lưu dữ liệu tại https://firebase.google.com/.
Khi làm tới đây, ta có thể sử dụng app để tạo các task và lưu vào database trên firebase.

- Hiển thị những task đã được lưu
Thêm vào file ***tasks.js*** trong thư mục *routes*:
```javascript
  model() {
    return this.store.findAll('task');
```
Thêm vào file ***tasks.hbs***
```javascript
{{#each model as |task|}}
<div class="well">
  <h4>Title: {{#link-to 'tasks.edit' task.id}}{{task.title}}{{/link-to}}</h4>
  <small>Date: {{format-date task.date}}</small>
  <h4>Discription: {{task.description}}</h4>
</div>
{{/each}}
```

- Edit task
Tạo route edit
```sh
$ ember g route tasks/edit
```
Tạo controller edit
```sh
$ ember g controller tasks/edit
```

Thêm vào file ***edit.hbs***
```javascript
<form>
  <div class="form-group">
    <label>Title</label>
    {{input type="text" class="form-control" value=model.title placeholder="Title of task..."}}
  </div>
  <div class="form-group">
    <label>Date</label>
    {{input type="date" class="form-control" value=model.date}}
  </div>
  <div class="form-group">
    <label>Description</label>
    {{textarea class="form-control" value=model.description placeholder="Descripton task..."}}
  </div>
  <button {{action 'editTask' model.id}} class="btn btn-primary">Save</button>
</form>
```
Thêm vào file ***edit.js*** trong thư mục */controller/tasks*
```javascript
export default Ember.Controller.extend({
  actions: {
    editTask: function(id){
      var self = this;
      var title = this.get('model.title');
      var description = this.get('model.description');
      var date = this.get('model.date');

      //update task
      this.store.findRecord('task', id).then(function(task){
        task.set('title', title);
        task.set('description', description);
        task.set('date', new Date(date));

        //save to database
        task.save();
        self.transitionTo('task');
      });
    }
  }
});
```

- Xóa task
Thêm vào file ***task.hbs***
```javascript
  <button {{action 'deleteTask' task.id}} class="btn btn-danger">Delete</button>
```
Thêm vào file ***tasks.js*** trong thư mục */controller*
```javascript
export default Ember.Controller.extend({
  actions: {
    deleteTask: function(id) {
      this.store.findRecord('task', id).then(function(task){
        task.deleteRecord();

        task.save();
      });
    }
  }
});
```

# Như vậy, ta đã hoàn thành xong việc cài đặt TaskApp bằng EmberJS #

![tasks](/images/sudung1.png)

![tasks](/images/sudung2.png)
