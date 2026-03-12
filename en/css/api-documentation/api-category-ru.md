Источник (EN): [api-category.md](./api-category.md)

# Категории API

## API Live Pad

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [CreateLivePadTemplate](https://www.tencentcloud.com/document/api/267/71831) | Создание шаблона live pad | 20 |
| [CreateLivePadRule](https://www.tencentcloud.com/document/api/267/71832) | Создание правила live pad | 20 |
| [StartLivePadStream](https://www.tencentcloud.com/document/api/267/70664) | StartLivePadStream | 20 |
| [StopLivePadStream](https://www.tencentcloud.com/document/api/267/71611) | StopLivePadStream | 20 |

## API транскодирования LVB

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [DeleteLiveTranscodeRule](https://www.tencentcloud.com/document/api/267/30789) | Удаление правила транскодирования | 200 |
| [DeleteLiveTranscodeTemplate](https://www.tencentcloud.com/document/api/267/30788) | Удаление шаблона транскодирования | 200 |
| [DescribeLiveTranscodeRules](https://www.tencentcloud.com/document/api/267/30787) | Получение списка правил транскодирования | 500 |
| [DescribeLiveTranscodeTemplate](https://www.tencentcloud.com/document/api/267/30786) | Получение одного шаблона транскодирования | 500 |
| [DescribeLiveTranscodeTemplates](https://www.tencentcloud.com/document/api/267/30785) | Получение списка шаблонов транскодирования | 500 |
| [CreateLiveTranscodeTemplate](https://www.tencentcloud.com/document/api/267/30790) | Создание шаблона транскодирования | 200 |
| [ModifyLiveTranscodeTemplate](https://www.tencentcloud.com/document/api/267/30784) | Изменение конфигурации шаблона транскодирования | 200 |
| [CreateLiveTranscodeRule](https://www.tencentcloud.com/document/api/267/30791) | Создание правила транскодирования | 200 |

## API управления отложенным воспроизведением

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [DescribeLiveDelayInfoList](https://www.tencentcloud.com/document/api/267/33532) | Получение списка отложенных воспроизведений | 500 |
| [ResumeDelayLiveStream](https://www.tencentcloud.com/document/api/267/30849) | Отмена задержки прямой трансляции | 200 |
| [AddDelayLiveStream](https://www.tencentcloud.com/document/api/267/30850) | Установка задержки прямой трансляции | 200 |

## API управления доменными именами

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [AddLiveDomain](https://www.tencentcloud.com/document/api/267/35189) | Добавление доменного имени | 100 |
| [AuthenticateDomainOwner](https://www.tencentcloud.com/document/api/267/50612) | Проверка владения доменом | 20 |
| [DeleteLiveDomain](https://www.tencentcloud.com/document/api/267/35188) | Удаление доменного имени | 100 |
| [DescribeLiveDomain](https://www.tencentcloud.com/document/api/267/35187) | Запрос информации о доменном имени | 500 |
| [DescribeLiveDomains](https://www.tencentcloud.com/document/api/267/35186) | Запрос списка доменных имён | 200 |
| [EnableLiveDomain](https://www.tencentcloud.com/document/api/267/35185) | Включение доменного имени | 100 |
| [ForbidLiveDomain](https://www.tencentcloud.com/document/api/267/35184) | Отключение доменного имени | 100 |
| [ModifyLivePlayDomain](https://www.tencentcloud.com/document/api/267/35183) | Изменение доменного имени воспроизведения | 200 |

## API управления водяными знаками

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [AddLiveWatermark](https://www.tencentcloud.com/document/api/267/30826) | Добавление водяного знака | 100 |
| [CreateLiveWatermarkRule](https://www.tencentcloud.com/document/api/267/30825) | Создание правила водяного знака | 200 |
| [DeleteLiveWatermark](https://www.tencentcloud.com/document/api/267/30824) | Удаление водяного знака | 100 |
| [DeleteLiveWatermarkRule](https://www.tencentcloud.com/document/api/267/30823) | Удаление правила водяного знака | 200 |
| [DescribeLiveWatermark](https://www.tencentcloud.com/document/api/267/30822) | Получение информации об одном водяном знаке | 500 |
| [DescribeLiveWatermarkRules](https://www.tencentcloud.com/document/api/267/30821) | Получение списка правил водяных знаков | 500 |
| [DescribeLiveWatermarks](https://www.tencentcloud.com/document/api/267/30820) | Запрос списка водяных знаков | 500 |
| [UpdateLiveWatermark](https://www.tencentcloud.com/document/api/267/30818) | Обновление водяного знака | 100 |

## API управления сертификатами

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [DescribeLiveCert](https://www.tencentcloud.com/document/api/267/30779) | Получение информации о сертификате | 500 |
| [DescribeLiveCerts](https://www.tencentcloud.com/document/api/267/30778) | Получение списка информации о сертификатах | 500 |
| [DescribeLiveDomainCert](https://www.tencentcloud.com/document/api/267/30777) | Получение информации о сертификате доменного имени | 500 |
| [DescribeLiveDomainCertBindings](https://www.tencentcloud.com/document/api/267/49645) | Запрос доменов, привязанных к сертификатам | 20 |
| [ModifyLiveDomainCertBindings](https://www.tencentcloud.com/document/api/267/49644) | Привязка сертификата к нескольким доменам воспроизведения | 20 |
| [UnBindLiveDomainCert](https://www.tencentcloud.com/document/api/267/30774) | Отвязка сертификата доменного имени | 200 |

## API микширования потоков

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [CancelCommonMixStream](https://www.tencentcloud.com/document/api/267/35998) | Отмена общего микширования потоков | 100 |
| [CreateCommonMixStream](https://www.tencentcloud.com/document/api/267/35997) | Создание общего микширования потоков | 200 |

## API извлечения потоков

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [DeleteLivePullStreamTask](https://www.tencentcloud.com/document/api/267/48356) | Удаление задачи извлечения потока | 50 |
| [DescribeLivePullStreamTasks](https://www.tencentcloud.com/document/api/267/48355) | Запрос задач извлечения потоков | 30 |
| [RestartLivePullStreamTask](https://www.tencentcloud.com/document/api/267/56967) | RestartLivePullStreamTask | 20 |
| [CreateLivePullStreamTask](https://www.tencentcloud.com/document/api/267/48357) | Создание задачи извлечения потока | 50 |
| [ModifyLivePullStreamTask](https://www.tencentcloud.com/document/api/267/48354) | Изменение задачи извлечения потока | 20 |

## API управления записью

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [CreateLiveRecord](https://www.tencentcloud.com/document/api/267/30847) | Создание задачи записи (устарел; используйте новый API) | 500 |
| [CreateLiveRecordRule](https://www.tencentcloud.com/document/api/267/30846) | Создание правила записи | 200 |
| [CreateLiveRecordTemplate](https://www.tencentcloud.com/document/api/267/30845) | Создание шаблона записи | 200 |
| [CreateRecordTask](https://www.tencentcloud.com/document/api/267/37309) | Создание задачи записи (новый) | 20 |
| [DeleteLiveRecord](https://www.tencentcloud.com/document/api/267/30844) | Удаление задачи записи (устарел; используйте новый API) | 200 |
| [DeleteLiveRecordRule](https://www.tencentcloud.com/document/api/267/30843) | Удаление правила записи | 200 |
| [DeleteLiveRecordTemplate](https://www.tencentcloud.com/document/api/267/30842) | Удаление шаблона записи | 200 |
| [DeleteRecordTask](https://www.tencentcloud.com/document/api/267/37308) | Удаление задачи записи (новый) | 20 |
| [DescribeLiveRecordRules](https://www.tencentcloud.com/document/api/267/30841) | Получение списка правил записи | 500 |
| [DescribeLiveRecordTemplate](https://www.tencentcloud.com/document/api/267/30840) | Получение одного шаблона записи | 500 |
| [DescribeLiveRecordTemplates](https://www.tencentcloud.com/document/api/267/30839) | Получение списка шаблонов записи | 500 |
| [DescribeRecordTask](https://www.tencentcloud.com/document/api/267/56133) | CreateRecordTask (новый) | 20 |
| [ModifyLiveRecordTemplate](https://www.tencentcloud.com/document/api/267/30838) | Изменение шаблона записи | 200 |
| [StopLiveRecord](https://www.tencentcloud.com/document/api/267/30837) | Остановка задачи записи (устарел; используйте новый API) | 200 |
| [StopRecordTask](https://www.tencentcloud.com/document/api/267/37307) | Остановка задачи записи (API) | 20 |

## API сдвига времени

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [CreateLiveTimeShiftRule](https://www.tencentcloud.com/document/api/267/53726) | Создание правила сдвига времени | 20 |
| [CreateLiveTimeShiftTemplate](https://www.tencentcloud.com/document/api/267/53725) | Создание шаблона сдвига времени | 20 |
| [DeleteLiveTimeShiftRule](https://www.tencentcloud.com/document/api/267/53724) | Удаление правила сдвига времени | 20 |
| [DeleteLiveTimeShiftTemplate](https://www.tencentcloud.com/document/api/267/53723) | Удаление шаблона сдвига времени | 20 |
| [DescribeLiveTimeShiftRules](https://www.tencentcloud.com/document/api/267/53722) | Запрос правил сдвига времени | 20 |
| [DescribeLiveTimeShiftTemplates](https://www.tencentcloud.com/document/api/267/53721) | Запрос шаблонов сдвига времени | 20 |
| [DescribeTimeShiftRecordDetail](https://www.tencentcloud.com/document/api/267/53720) | Запрос деталей сдвига времени | 20 |
| [DescribeTimeShiftStreamList](https://www.tencentcloud.com/document/api/267/53719) | Запрос потоков со сдвигом времени | 20 |
| [ModifyLiveTimeShiftTemplate](https://www.tencentcloud.com/document/api/267/53718) | Изменение шаблона резервного потока | 20 |

## API обратных вызовов LVB

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [CreateLiveCallbackRule](https://www.tencentcloud.com/document/api/267/30816) | Создание правила обратного вызова | 200 |
| [CreateLiveCallbackTemplate](https://www.tencentcloud.com/document/api/267/30815) | Создание шаблона обратного вызова | 200 |
| [DeleteLiveCallbackRule](https://www.tencentcloud.com/document/api/267/30814) | Удаление правила обратного вызова | 200 |
| [DeleteLiveCallbackTemplate](https://www.tencentcloud.com/document/api/267/30813) | Удаление шаблона обратного вызова | 200 |
| [DescribeLiveCallbackRules](https://www.tencentcloud.com/document/api/267/30812) | Получение списка правил обратных вызовов | 500 |
| [DescribeLiveCallbackTemplate](https://www.tencentcloud.com/document/api/267/30811) | Получение шаблона обратного вызова | 500 |
| [DescribeLiveCallbackTemplates](https://www.tencentcloud.com/document/api/267/30810) | Получение списка шаблонов обратных вызовов | 500 |
| [ModifyLiveCallbackTemplate](https://www.tencentcloud.com/document/api/267/30809) | Изменение шаблона обратного вызова | 200 |

## API создания снимков экрана и обнаружения порнографии

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [CreateLiveSnapshotRule](https://www.tencentcloud.com/document/api/267/30835) | Создание правила создания снимков экрана | 200 |
| [CreateLiveSnapshotTemplate](https://www.tencentcloud.com/document/api/267/30834) | Создание шаблона создания снимков экрана | 200 |
| [CreateScreenshotTask](https://www.tencentcloud.com/document/api/267/54799) | Создание задачи создания снимков экрана | 20 |
| [DeleteLiveSnapshotRule](https://www.tencentcloud.com/document/api/267/30833) | Удаление правила создания снимков экрана | 200 |
| [DeleteLiveSnapshotTemplate](https://www.tencentcloud.com/document/api/267/30832) | Удаление шаблона создания снимков экрана | 200 |
| [DescribeLiveSnapshotRules](https://www.tencentcloud.com/document/api/267/30831) | Получение списка правил создания снимков экрана | 500 |
| [DescribeLiveSnapshotTemplate](https://www.tencentcloud.com/document/api/267/30830) | Получение одного шаблона создания снимков экрана | 500 |
| [DescribeLiveSnapshotTemplates](https://www.tencentcloud.com/document/api/267/30829) | Получение списка шаблонов создания снимков экрана | 500 |
| [ModifyLiveSnapshotTemplate](https://www.tencentcloud.com/document/api/267/30828) | Изменение конфигурации шаблона создания снимков экрана | 200 |

## API управления аутентификацией

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [DescribeLiveDomainReferer](https://www.tencentcloud.com/document/api/267/40611) | Запрос конфигурации белого/чёрного списка referer для домена прямой трансляции | 20 |
| [DescribeLivePlayAuthKey](https://www.tencentcloud.com/document/api/267/30772) | Запрос ключа аутентификации воспроизведения | 500 |
| [DescribeLivePushAuthKey](https://www.tencentcloud.com/document/api/267/30771) | Запрос ключа аутентификации push | 500 |
| [ModifyLiveDomainReferer](https://www.tencentcloud.com/document/api/267/40610) | Настройка белого/чёрного списка referer для домена прямой трансляции | 20 |
| [ModifyLivePlayAuthKey](https://www.tencentcloud.com/document/api/267/30770) | Изменение ключа аутентификации воспроизведения | 100 |
| [ModifyLivePushAuthKey](https://www.tencentcloud.com/document/api/267/30769) | Изменение ключа аутентификации push | 200 |

## API запроса данных мониторинга

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [DescribeAllStreamPlayInfoList](https://www.tencentcloud.com/document/api/267/37306) | Получение данных воспроизведения всех потоков на указанный момент времени | 20 |
| [DescribeGroupProIspPlayInfoList](https://www.tencentcloud.com/document/api/267/36097) | Запрос данных нисходящего воспроизведения по региону и провайдеру | 200 |
| [DescribeHttpStatusInfoList](https://www.tencentcloud.com/document/api/267/37305) | Запрос деталей по каждому HTTP-коду статуса воспроизведения | 200 |
| [DescribeLiveStreamPushInfoList](https://www.tencentcloud.com/document/api/267/37303) | Получение данных push прямых трансляций | 500 |
| [DescribePlayErrorCodeDetailInfoList](https://www.tencentcloud.com/document/api/267/37301) | Запрос данных в реальном времени по каждому HTTP-коду ошибки воспроизведения | 100 |
| [DescribePlayErrorCodeSumInfoList](https://www.tencentcloud.com/document/api/267/37300) | Запрос агрегированных данных по HTTP-кодам ошибок воспроизведения | 200 |
| [DescribeProvinceIspPlayInfoList](https://www.tencentcloud.com/document/api/267/37299) | Запрос информации о воспроизведении по провайдеру и региону | 200 |
| [DescribeStreamDayPlayInfoList](https://www.tencentcloud.com/document/api/267/36095) | Запрос данных трафика всех потоков | 500 |
| [DescribeStreamPlayInfoList](https://www.tencentcloud.com/document/api/267/37297) | Запрос списка информации о воспроизведении потока | 500 |
| [DescribeStreamPushInfoList](https://www.tencentcloud.com/document/api/267/36094) | Получение данных push потока | 40 |
| [DescribeTopClientIpSumInfoList](https://www.tencentcloud.com/document/api/267/37296) | Запрос информации о топ-n IP-адресах клиентов за определённый период | 100 |
| [DescribeVisitTopSumInfoList](https://www.tencentcloud.com/document/api/267/37295) | Запрос информации о топ-n доменных именах или идентификаторах потоков за определённый период | 100 |
| [DescribeLiveTranscodeDetailInfo](https://www.tencentcloud.com/document/api/267/37302) | Запрос статистики транскодирования LVB | 200 |

## API запроса данных биллинга

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [DescribeDeliverBandwidthList](https://www.tencentcloud.com/document/api/267/37836) | Запрос оплачиваемой полосы пропускания ретрансляции прямой трансляции | 20 |
| [DescribeLiveTimeShiftBillInfoList](https://www.tencentcloud.com/document/api/267/47919) | Запрос данных биллинга сдвига времени | 20 |
| [DescribeLiveTranscodeTotalInfo](https://www.tencentcloud.com/document/api/267/44907) | Запрос общего использования сервиса транскодирования | 200 |
| [DescribeScreenShotSheetNumList](https://www.tencentcloud.com/document/api/267/37298) | Запрос количества снимков экрана | 100 |
| [DescribeTranscodeTaskNum](https://www.tencentcloud.com/document/api/267/50613) | Запрос количества задач транскодирования | 20 |
| [DescribeUploadStreamNums](https://www.tencentcloud.com/document/api/267/39500) | Запрос количества входящих каналов LVB | 20 |
| [DescribeConcurrentRecordStreamNum](https://www.tencentcloud.com/document/api/267/36188) | Запрос количества одновременных каналов записи | 200 |
| [DescribeBillBandwidthAndFluxList](https://www.tencentcloud.com/document/api/267/36098) | Запрос данных оплачиваемой полосы пропускания и трафика | 100 |

## API управления прямыми трансляциями

| Название API | Функция | Ограничение частоты (максимум запросов в секунду) |
| --- | --- | --- |
| [DescribeLiveForbidStreamList](https://www.tencentcloud.com/document/api/267/30801) | Получение списка заблокированных потоков | 100 |
| [DescribeLiveStreamEventList](https://www.tencentcloud.com/document/api/267/30800) | Запрос событий потоковой передачи | 300 |
| [DescribeLiveStreamOnlineList](https://www.tencentcloud.com/document/api/267/30798) | Запрос активных прямых трансляций | 100 |
| [DescribeLiveStreamPublishedList](https://www.tencentcloud.com/document/api/267/30797) | Запрос списка отправленных потоков | 300 |
| [DropLiveStream](https://www.tencentcloud.com/document/api/267/30795) | Приостановка прямой трансляции | 100 |
| [ResumeLiveStream](https://www.tencentcloud.com/document/api/267/30793) | Возобновление прямой трансляции | 100 |
| [DescribeLiveStreamState](https://www.tencentcloud.com/document/api/267/30796) | Запрос состояния потока | 300 |
| [ForbidLiveStream](https://www.tencentcloud.com/document/api/267/30794) | Блокировка прямой трансляции | 200 |


---
*Source: [https://www.tencentcloud.com/document/product/267/30760](https://www.tencentcloud.com/document/product/267/30760)*
