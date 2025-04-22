#  Student Feedback System Project in Django with Source Code

The **Student Feedback System in Django created based on Python, Django, and SQLITE3 Database**.

The **Student Feedback System is a simple project for College Students** has been developed with the aim of rating and analyzing the success of college faculty.

This form of Student Feedback system eliminates the time-consuming task of manually inspecting each student’s feedback pages.

A Student Feedback System Project alleviates the time and effort required to keep and maintain records on a manual basis, which necessitates a lot of space and security.

In the case of paper-based feedbacks, students’ feedbacks can also be tempered for the wrong reasons, but the Student Feedback system can still guarantee the privacy of feedbacks.

This **Student Feedback System in Django** is an easy project for beginners to learn how to build a web-based python Django project.

We will provide you with the complete source code and database for the python project so that you can easily install it on your machine and learn how to program in Python Django.

>[!NOTE]
> To start creating a **Student Feedback System Project in Python Django**, makes sure that you have PyCharm Professional IDE Installed in your computer.

## Front end Features

* **Login Page**

Student enter their credentials on this page to gain access in the system.

* **Home Page**

When student visit the system, this is the system’s default page. This page shows the books for sale in the store, or by entering a keyword in the search box above the books.

* **View Profile**

Student can view their profile.

* **Update Profile**

Student can update their profile

* **Change Password**

Student can update their Password for the security of their account.

* **Send Feedback**

Student can choose faculty and give feedback.

## How to Create a Student Feedback System in Django?

Here are the steps on **how to create a Student Feedback System Project in Django with Source Code**.

1. **Open file**.

First, open “pycharm professional” after that click “file” and click “new project”.

![image](https://github.com/user-attachments/assets/dadc81c6-3b8a-4788-8e9c-b207b7afdaa8)


2. **Choose Django**.

Next, after click “new project”, choose “Django” and click.

![image](https://github.com/user-attachments/assets/01becef3-4e28-42c4-8238-ec87f7838bac)


3. **Select file location**.

Then, select a file location wherever you want.

4. **Create application name.**

After that, name your application.

5. **Click create.**

Lastly, finish creating project by clicking “create” button.

6. **Start Coding**.

Finally, we will now start adding functionality to our Django Framework by adding some functional codes.

## Functionality and Codes

* **Create template for the sidebar**

In this section, we will learn on how create a templates for the sidebar. 

To start with, add the following code in your sidebar_template.html under the folder of /templates/student_template.

```
{% load static %}

<aside class="main-sidebar sidebar-dark-primary elevation-4">
      <!-- Brand Logo -->
      <a href="{% url 'student_home' %}" class="brand-link">
        <img src="{% static 'dist/img/chmsc.jpg' %}" alt="AdminLTE Logo" class="brand-image img-circle elevation-3"
            style="opacity: .8">
        <span class="brand-text font-weight-light">CHMSC - BINALBAGAN</span>
      </a>

      <!-- Sidebar -->
      <div class="sidebar">
        <!-- Sidebar user panel (optional) -->
        <div class="user-panel mt-3 pb-3 mb-3 d-flex">
          <div class="image">
            <img src="{% static 'dist/img/user2-160x160.jpg' %}" class="img-circle elevation-2" alt="User Image">
          </div>
          <div class="info">
            <a href="{% url 'student_profile' %}" class="d-block">{{ user.first_name }} {{ user.last_name }}</a>
          </div>
        </div>

        <!-- Sidebar Menu -->
        <nav class="mt-2">
          <ul class="nav nav-pills nav-sidebar flex-column" data-widget="treeview" role="menu" data-accordion="false">
            <!-- Add icons to the links using the .nav-icon class
                with font-awesome or any other icon font library -->
            
            <li class="nav-item">
              {% url 'student_home' as student_home %}
              <a href="{{ student_home }}" class="nav-link {% if request.path == student_home %} active {% endif %}">
                <i class="nav-icon fas fa-tachometer-alt"></i>
                <p>
                  Home
                  {% comment %} <span class="right badge badge-danger">New</span> {% endcomment %}
                </p>
              </a>
            </li>

            <li class="nav-item">
              {% url 'student_view_attendance' as student_view_attendance %}
              <a href="{{ student_view_attendance }}" class="nav-link {% if request.path == student_view_attendance %} active {% endif %}">
                <i class="nav-icon fas fa-calendar-alt"></i>
                <p>
                  View Attendance
                  {% comment %} <span class="right badge badge-danger">New</span> {% endcomment %}
                </p>
              </a>
            </li>

            <li class="nav-item">
              {% url 'student_view_result' as student_view_result %}
              <a href="{{ student_view_result }}" class="nav-link {% if request.path == student_view_result %} active {% endif %}">
                <i class="nav-icon fas fa-tasks"></i>
                <p>
                  View Result
                  {% comment %} <span class="right badge badge-danger">New</span> {% endcomment %}
                </p>
              </a>
            </li>

            <li class="nav-item">
              {% url 'student_apply_leave' as student_apply_leave %}
              <a href="{{ student_apply_leave }}" class="nav-link {% if request.path == student_apply_leave %} active {% endif %}">
                <i class="nav-icon fas fa-envelope-open-text"></i>
                <p>
                  Apply for Leave
                  {% comment %} <span class="right badge badge-danger">New</span> {% endcomment %}
                </p>
              </a>
            </li>

            <li class="nav-item">
              {% url 'student_feedback' as student_feedback %}
              <a href="{{ student_feedback }}" class="nav-link {% if request.path == student_feedback %} active {% endif %}">
                <i class="nav-icon fas fa-comments"></i>
                <p>
                  Send Feedback
                  {% comment %} <span class="right badge badge-danger">New</span> {% endcomment %}
                </p>
              </a>
            </li>

          </ul>
        </nav>
        <!-- /.sidebar-menu -->
      </div>
      <!-- /.sidebar -->
    </aside>
```

*  **Create template for the feedback form**

In this section, we will learn on how create a templates for the feedback form. 

To start with, add the following code in your student_feedback.html under the folder of /templates/student_template.

```
{% extends 'student_template/base_template.html' %}

{% block page_title %}
    Feedback Message
{% endblock page_title %}

{% block main_content %}

{% load static %}

<section class="content">
        <div class="container-fluid">

            <div class="row">
                <div class="col-md-12">
                    <!-- general form elements -->
                    <div class="card card-primary">
                    <div class="card-header">
                        <h3 class="card-title">Leave a Feedback Message</h3>
                    </div>
                    <!-- /.card-header -->

                                {% comment %} Display Messages {% endcomment %}
                                {% if messages %}
                                <div class="form-group">
                                <div class="col-12">
                                    {% for message in messages %}
                                    {% if message.tags == "error" %}
                                        <div class="alert alert-danger alert-dismissible fade show" role="alert" style="margin-top: 10px;">
                                        {{ message }}
                                        <button type="button" class="close" data-dismiss="alert" aria-label="Close">
                                            <span aria-hidden="true">&times;</span>
                                        </button>
                                        </div>
                                    {% elif message.tags == "success" %}
                                        <div class="alert alert-success alert-dismissible fade show" role="alert" style="margin-top: 10px;">
                                        {{ message }}
                                        <button type="button" class="close" data-dismiss="alert" aria-label="Close">
                                            <span aria-hidden="true">&times;</span>
                                        </button>
                                        </div>
                                    {% endif %}
                                    {% endfor %}
                                </div>
                                </div>
                                {% endif %}
                            
                    <form method="POST" action="{% url 'student_feedback_save' %}">
                        {% csrf_token %}
                        <div class="card-body">
                           
                            <div class="form-group">
                                <label>Feedback Message </label>
                                <textarea name="feedback_message" class="form-control" rows="6" placeholder="Feedback Message"></textarea>
                            </div>


                        </div>
                        <!-- /.card-body -->

                        <div class="card-footer">
                        <button type="submit" class="btn btn-primary">Leave a Feedback</button>
                        </div>

                    </form>

                    </div>
                    <!-- /.card -->



                </div>
            </div>

            <div class="row">
                <div class="col-md-12">
                    <div class="card card-success">
                        <div class="card-header">
                            <h3 class="card-title">Feedback History</h3>
                        </div>

                        <div class="card-body">
                           <div class="table-responsive">
                                <table class="table">
                                    <thead class="thead-light">
                                    <tr>
                                        <th>#ID</th>
                                        <th>Feedback Message</th>
                                        <th>Feedback Reply</th>
                                    </tr>
                                    </thead>
                                    
                                    {% for row in feedback_data %}
                                    <tr>
                                        <td>{{ row.id }}</td>
                                        <td>{{ row.feedback }}</td>
                                        <td>{{ row.feedback_reply }}</td>
                                    </tr>
                                    {% endfor %}
                                </table>
                            </div>
                        </div>
                        <!-- /.card-body -->
                    </div>
                </div>
            </div>

        </div><!-- /.container-fluid -->
      </section>

  {% endblock main_content %}

{% block custom_js %}

{% endblock custom_js %}
```

* Create template for the student profile form

In this section, we will learn on how create a templates for the student profile form. 

To start with, add the following code in your student_profile.html under the folder of /templates/student_profile.

```
{% extends 'student_template/base_template.html' %}

{% block page_title %}
    Update Profile
{% endblock page_title %}

{% block main_content %}

{% load static %}

<section class="content">
        <div class="container-fluid">

            <div class="row">
                <div class="col-md-12">
                    <!-- general form elements -->
                    <div class="card card-primary">
                    <div class="card-header">
                        <h3 class="card-title">Update Profile</h3>
                    </div>
                    <!-- /.card-header -->
                    <!-- form start -->
                    <form role="form" method="POST" action="{% url 'student_profile_update' %}">
                        {% csrf_token %}

                        
                                {% comment %} Display Messages {% endcomment %}
                                {% if messages %}
                                <div class="form-group">
                                <div class="col-12">
                                    {% for message in messages %}
                                    {% if message.tags == "error" %}
                                        <div class="alert alert-danger alert-dismissible fade show" role="alert" style="margin-top: 10px;">
                                        {{ message }}
                                        <button type="button" class="close" data-dismiss="alert" aria-label="Close">
                                            <span aria-hidden="true">&times;</span>
                                        </button>
                                        </div>
                                    {% elif message.tags == "success" %}
                                        <div class="alert alert-success alert-dismissible fade show" role="alert" style="margin-top: 10px;">
                                        {{ message }}
                                        <button type="button" class="close" data-dismiss="alert" aria-label="Close">
                                            <span aria-hidden="true">&times;</span>
                                        </button>
                                        </div>
                                    {% endif %}
                                    {% endfor %}
                                </div>
                                </div>
                                {% endif %}
                            

                        <div class="card-body">
                            <div class="form-group">
                                <label>Username </label>
                                <input type="text" class="form-control" name="username" value="{{ user.username }}" disabled="disabled">
                            </div>

                            <div class="form-group">
                                <label>Email </label>
                                <input type="text" class="form-control" name="email" value="{{ user.email }}" disabled="disabled">
                            </div>

                            <div class="form-group">
                                <label>First Name </label>
                                <input type="text" class="form-control" name="first_name" value="{{ user.first_name }}">
                            </div>

                            <div class="form-group">
                                <label>Last Name </label>
                                <input type="text" class="form-control" name="last_name" value="{{ user.last_name }}">
                            </div>

                            <div class="form-group">
                                <label>Address </label>
                                <textarea name="address" class="form-control" row="5">{{ student.address }}</textarea>
                            </div>

                            <div class="form-group">
                                <label>Password </label>
                                <input type="text" class="form-control" name="password" placeholder="Fill only if you want to change Password.">
                            </div>

                        </div>
                        <!-- /.card-body -->

                        <div class="card-footer">
                        <button type="submit" class="btn btn-primary">Update Profile</button>
                        </div>
                    </form>
                    </div>
                    <!-- /.card -->

                </div>
            </div>

        </div><!-- /.container-fluid -->
      </section>

  {% endblock main_content %}
```


### 📌Here's the full documentation for the [Student Feedback System Project in Django](https://itsourcecode.com/free-projects/python-projects/student-feedback-system-project-in-django-with-source-code/)
