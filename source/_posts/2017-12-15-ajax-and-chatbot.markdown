---
layout: post
title: "AJAX and Chatbot"
date: 2017-12-15 20:14
comments: true
categories: [computer]
tags: [AJAX,Chatbot,django]
---
AJAX是一个缩写，代表：Asynchronous JavaScript And XML.  

    AJAX is a developer's dream, because you can:
    # Read data from a web server - after the page has loaded
    # Update a web page without reloading the page
    # Send data to a web server - in the background

今天改写了一个代码实现了聊天的过程中不需要重新加载页面。代码如下：   

urls.py

    url(r'^api/chat/', post), 

view.py

    def post(request, *args, **kwargs):
        """
        Return a response to the statement in the posted data.
        """
        bot = ChatBot("Training Example")
        bot.set_trainer(ListTrainer)
        input_data = json.loads(request.read().decode('utf-8'))
        response = bot.get_response(input_data)
        response_data = response.serialize()
        return JsonResponse(response_data, status=200)

chat.html

    <script>
      var chatterbotUrl = '/api/chat/';
      var csrftoken = Cookies.get('csrftoken');
      function csrfSafeMethod(method) {
        // these HTTP methods do not require CSRF protection
        return (/^(GET|HEAD|OPTIONS|TRACE)$/.test(method));
      }

      $.ajaxSetup({
        beforeSend: function(xhr, settings) {
          if (!csrfSafeMethod(settings.type) && !this.crossDomain) {
            xhr.setRequestHeader("X-CSRFToken", csrftoken);
          }
        }
      });

      var $input = $('#input');
      var $sayButton = $('#sayButton');
      var $answer = $('#answer');

      function submitInput() {
        var inputData = {
          'text': $input.val()
        }
        var $submit = $.ajax({
          type: 'POST',
          url: chatterbotUrl,
          data: JSON.stringify(inputData),
          contentType: 'application/json'
        });

        $submit.done(function(statement) {
            $answer.val(statement.text);
            // Clear the input field
            $input.val('');
            //alert(statement.text)
        });

      $sayButton.click(function() {
        submitInput();
      });


原理是这样的，首先你需要通过urls.py文件指定在请求特定url的时候，触发的函数。这个函数是在view.py中定义的，也就是post函数。post函数需要至少一个参数，也就是request，request必须包含一个text的属性才能被read()出来而不出错。之后，post函数会返回一个JsonResponse，其中机器人的回答可以通过statement.text来获取和使用，见chat.html中的$submit.done函数。  

当不知道传递的是何值时，可以通过html 中的alert或者python中的print（）来监听调试。
