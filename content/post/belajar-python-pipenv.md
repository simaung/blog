---
title: "Belajar Python: Pipenv"
date: 2019-01-08T17:42:35+07:00
draft: false
---
**Pipenv** merupakan suatu lingkungan *virtual environment* mirip dengan [**venv**](../virtual-environtment) yang telah kita bahas sebelumnya.

#### Install pipenv
Untuk menginstall pipenv gunakan perintah seperti dibawah ini, pastikan **pip** sudah terpasang di sistem kamu ya.
{{< highlight bash >}}
$ pip install pipenv
{{< /highlight >}}

#### Penggunaan pipenv
untuk menggunakan pipenv gunakan perintah **pipenv shell** untuk membuat lingkungan virtual di lokasi default dari pipenv,
{{< highlight bash >}}
$ pipenv shell

Creating a virtualenv for this project…
Pipfile: /home/aliya-azka/myproject/python/2019/api/back_learn_boilerplate/Pipfile
Using /usr/local/bin/python3.7 (3.7.4) to create virtualenv…
⠸ Creating virtual environment...Already using interpreter /usr/local/bin/python3.7
Using base prefix '/usr/local'
New python executable in /home/aliya-azka/.local/share/virtualenvs/back_learn_boilerplate-KhnJXOgt/bin/python3.7
Also creating executable in /home/aliya-azka/.local/share/virtualenvs/back_learn_boilerplate-KhnJXOgt/bin/python
Installing setuptools, pip, wheel...
done.

✔ Successfully created virtual environment! 
Virtualenv location: /home/aliya-azka/.local/share/virtualenvs/back_learn_boilerplate-KhnJXOgt
Creating a Pipfile for this project…
Launching subshell in virtual environment…
 . /home/aliya-azka/.local/share/virtualenvs/back_learn_boilerplate-KhnJXOgt/bin/activate
➜  back_learn_boilerplate  . /home/aliya-azka/.local/share/virtualenvs/back_learn_boilerplate-KhnJXOgt/bin/activate
{{< /highlight >}}
Dengan mengetikkan perintah tersebut maka otomatis akan membuat file bernama **Pipfile** pada lokasi direktori dimana perintah tersebut di eksekusi.


#### Memasang package python dengan pipenv
Untuk memasang package python gunakan perintah **pipenv install [nama-package]**, berikut contoh untuk memasang package **Flask**
{{< highlight bash >}}
(back_learn_boilerplate) ➜  back_learn_boilerplate pipenv install flask
Installing flask…
Adding flask to Pipfile's [packages]…
✔ Installation Succeeded 
Pipfile.lock not found, creating…
Locking [dev-packages] dependencies…
Locking [packages] dependencies…
✔ Success! 
Updated Pipfile.lock (662286)!
Installing dependencies from Pipfile.lock (662286)…
  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 6/6 — 00:00:06

{{< /highlight >}}
Setelah kita memasang package menggunakan pipenv maka akan terbentuk file dengan nama **Pipfile.lock**, catatan jangan pernah merubah file ini ya.
