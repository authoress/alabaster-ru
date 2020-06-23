=========
Установка
=========

Для установки Alabaster минимально необходимо следующее:

* Если вы используете **Sphinx 1.2 или ниже**:

    * Выполните команду ``pip install alabaster`` или ее аналог.
    * Добавьте следующие строки в ``conf.py``, чтобы тема Alabaster и
      мини-расширение для нее стали доступны:

       .. code-block:: python

            import alabaster

            html_theme_path = [alabaster.get_path()]
            extensions = ['alabaster']
            html_theme = 'alabaster'

    * Если вы установили Alabaster вручную (без использования ``pip``) или
      развлекаетесь с PYTHONPATH, вам может потребоваться вместо
      вызова ``alabaster.get_path()`` явно прописать путь к Alabaster в соответствии с
      `документацией по настройке Sphinx
      <http://sphinx-doc.org/config.html#confval-html_theme_path>`_.

* Если у вас **Sphinx 1.3 или выше**:

    * Alabaster уже установлен как зависимость! Нет необходимости вручную
      устанавливать или явно загружать его.

      .. note::
        Если вы распространяете свою документацию через `Read the Docs
        <https://readthedocs.org>`_, вам может потребоваться явно включить
        Alabaster, поскольку Read the Docs по умолчанию использует собственную тему. Добавьте эту строку
        в ``conf.py``::

            html_theme = 'alabaster'

* **В любом случае**, добавьте явную настройку ``html_sidebars``, чтобы
  загрузились шаблоны боковой панели Alabaster:
   
   .. code-block:: python
    
        html_sidebars = {
            '**': [
                'about.html',
                'navigation.html',
                'relations.html',
                'searchbox.html',
                'donate.html',
            ]
        }

Вот и все! Теперь у вас есть стандартная тема Alabaster. Продолжайте читать, чтобы узнать больше о
ключевых моментах конфигурации, или перейдите в раздел :doc:`customization`, где описана
настройка свойств и стилей.


Боковые панели
--------------

Настраивайте ``html_sidebars`` по желанию — тема разработана,
исходя из предположения, что у вас всегда будет включен ``about.html``, но в отношении остальных элементов
это не обязательно.

* Смотрите `документацию Sphinx
  <http://sphinx-doc.org/config.html#confval-html_sidebars>`_, чтобы узнать больше о том,
  как работает эта настройка.
* Alabaster предоставляет ``about.html`` (логотип, кнопка github и краткое описание проекта),
  ``donate.html`` (кнопки / ссылки для пожертвований и поддержки) и ``navigation.html``
  (более гибкая версия встроенных шаблонов ``localtoc`` и ``globaltoc``).
  Боковая панель поиска (``searchbox.html``) поставляется со Sphinx.


.. _static-path:

Статический путь для изображений и пользовательских таблиц стилей
-----------------------------------------------------------------

Если вы используете какой-либо из параметров изображений, перечисленных в разделе :doc:`customization`
(``logo`` или ``touch-icon``), или :ref:`пользовательскую таблицу стилей <custom-stylesheet>`,
вам также нужно указать Sphinx, откуда взять эти файлы. Если так, добавьте
вот такую строку (изменив пути, если необходимо; см. `документацию Sphinx для
'html_static_path'
<http://sphinx-doc.org/config.html?highlight=static#confval-html_static_path>`_) в ваш ``conf.py``:

.. code-block:: python

    html_static_path = ['_static']
