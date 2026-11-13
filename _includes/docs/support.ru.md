{% comment %}
Support page template, Russian. One template per language; the {% raw %}{% if app.* %}{% endraw %}
switches and _data/apps.yml fit it to each app. Keep the six languages in step. App-specific questions come from app.faq in _data/apps.yml.
Do not indent lines (Markdown would turn them into code blocks).
{% endcomment %}
# {{ t.support }}

Вопросы, ошибки, идеи? Пишите на **[{{ email }}]({{ mailto }})** — обычно мы отвечаем в течение {{ studio.support.response_days }} рабочих дней. Укажите, пожалуйста, модель устройства, версию ОС и версию приложения.

{% if studio.support.form_url != "" %}Или воспользуйтесь формой ниже:

<iframe class="support-form" src="{{ studio.support.form_url }}" title="Форма поддержки" loading="lazy"></iframe>
{% endif %}

## Частые вопросы

{% if app.iap %}{% if app.iap_plans %}**Я купил(а) тариф, но он не разблокирован.**<br>
Откройте в приложении экран тарифов или Настройки и нажмите **Восстановить покупки**, войдя в ту же учётную запись Google, с которой вы покупали.{% else %}**Я купил(а) {{ app.premium_name }}, но он не разблокирован.**<br>
{% if app.restore_note %}{{ app.restore_note[lang] }}{% else %}Откройте экран {{ app.premium_name }} в приложении и нажмите **Восстановить покупку**, войдя в ту же учётную запись Apple или Google, с которой вы покупали.{% endif %}{% endif %}

**Как вернуть деньги?**<br>
Возврат средств выполняет магазин: [Apple](https://reportaproblem.apple.com) · [Google Play](https://support.google.com/googleplay/answer/2479637).

{% endif %}{% for item in app.faq %}**{{ item.q[lang] }}**<br>
{{ item.a[lang] }}

{% endfor %}**Где хранятся мои данные?**<br>
{% if app.data_location[lang] %}{{ app.data_location[lang] }}{% elsif app.accounts %}В вашей учётной записи на наших серверах — см. политику конфиденциальности.{% else %}Только на вашем устройстве. У нас нет учётных записей и серверов.{% endif %}

{% if app.delete_data_path[lang] %}**Как удалить мои данные?**<br>
{% if app.accounts %}«{{ app.delete_data_path[lang] }}» удаляет данные на телефоне{% if app.telegram %} и отключает Telegram{% endif %}; удаление приложения делает то же самое для телефона. Чтобы удалить также вашу запись на нашем сервере, напишите нам — см. [политику конфиденциальности]({{ privacy_url }}).{% else %}{{ app.delete_data_path[lang] }}. {% if app.delete_data_note %}{{ app.delete_data_note[lang] }}{% else %}Удаление приложения тоже стирает всё.{% endif %}{% endif %}

{% endif %}{% if app.ads %}{% if app.ads_consent == false %}**Как ограничить персонализацию рекламы?**<br>
В настройках устройства (Android: Настройки → Google → Реклама или Настройки → Конфиденциальность → Реклама).{% if app.iap %} {% if app.ads_paid_note %}{{ app.ads_paid_note[lang] }}{% else %}{{ app.premium_name }} полностью убирает рекламу.{% endif %}{% endif %}{% else %}**Как изменить согласие на рекламу?**<br>
{% if app.ads_privacy_path[lang] %}В разделе **{{ app.ads_privacy_path[lang] }}**{% else %}В настройках приложения, в разделе настроек конфиденциальности рекламы{% endif %} (показывается в ЕЭЗ, Великобритании и Швейцарии, где требуется согласие).{% if app.iap %} {% if app.ads_paid_note %}{{ app.ads_paid_note[lang] }}{% else %}{{ app.premium_name }} полностью убирает рекламу.{% endif %}{% endif %}{% endif %}

{% endif %}## Правовая информация

[{{ t.privacy }}]({{ privacy_url }}) · [{{ t.terms }}]({{ terms_url }}) · [{{ t.legal_notice }}]({{ '/legal-notice/' | relative_url }})
