---
title: Contact

form:
    name: contact

    fields:
        - name: name
          label: Name
          placeholder: Enter your name
          autofocus: on
          autocomplete: on
          type: text
          validate:
            required: true

        - name: email
          label: Email
          placeholder: Enter your email address
          type: email
          validate:
            required: true

        - name: message
          label: Message
          placeholder: Enter your message
          type: textarea
          validate:
            required: true

        - name: g-recaptcha-response
          label: Captcha
          type: captcha
          recatpcha_site_key: 6LcgnQkUAAAAAFlfFrVFtqcqMegPtTGvdkNCkFPz
          recaptcha_not_validated: 'Captcha not valid!'
          validate:
            required: true

    buttons:
        - type: submit
          value: Submit
        - type: reset
          value: Reset

    process:
        - captcha:
            recatpcha_secret: 6LcgnQkUAAAAABZgEPoHHhGkhprj56JeL8IJm8NO
        - email:
            subject: "{{ form.value.name|e }} messaged you via justin.mulwee.com"
            body: "{{ form.value.message }}"
            from: "{{ form.value.email }}"
            from_name: "{{ form.value.name }}"
        - save:
            fileprefix: contact-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        - message: Thank you for getting in touch!
        - display: thankyou
---

# Contact Justin

I know some people ignore their contact form, but whether it's personal or professional I read every message and usually reply by the next day.