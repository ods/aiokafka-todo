<hr/>

https://github.com/aio-libs/aiokafka/actions/runs/5123049614/jobs/9213090496

`tests/test_consumer.py::TestConsumerIntegration::test_check_extended_message_record` (after failed `tests/test_conn.py::ConnIntegrationTest::test_send_without_response`)

```
E               pytest.PytestUnraisableExceptionWarning: Exception ignored in: <coroutine object StreamWriter.drain at 0x7f1f312cb610>
E
E               Traceback (most recent call last):
E                 File "/opt/hostedtoolcache/Python/3.10.11/x64/lib/python3.10/warnings.py", line 506, in _warn_unawaited_coroutine
E                   warn(msg, category=RuntimeWarning, stacklevel=2, source=coro)
E               RuntimeWarning: coroutine 'StreamWriter.drain' was never awaited
```

<hr/>

https://github.com/ods/aiokafka/actions/runs/5431828005/jobs/9878455324

`tests/test_transactional_consumer.py::TestKafkaConsumerIntegration::test_consumer_transactional_commit`

```
        # The transaction blocked consumption
        task = create_task(consumer.getone())
        await asyncio.sleep(1)
>       self.assertFalse(task.done())
E       AssertionError: True is not false
```

<hr/>

https://github.com/ods/aiokafka/actions/runs/6882395215/job/18720877333

`tests/test_consumer.py::TestConsumerIntegration::test_consumer_fast_unsubscribe`

```
>                   assignment = self._subscriptions.subscription.assignment
E                   AttributeError: 'NoneType' object has no attribute 'assignment'

aiokafka/consumer/fetcher.py:509: AttributeError

During handling of the above exception, another exception occurred:

>       await consumer.stop()

tests/test_consumer.py:1604:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
aiokafka/consumer/consumer.py:492: in stop
    await self._fetcher.close()
aiokafka/consumer/fetcher.py:427: in close
    await self._fetch_task
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

>           raise Errors.KafkaError("Unexpected error during data retrieval")
E           aiokafka.errors.KafkaError: KafkaError: Unexpected error during data retrieval
```

`tests/test_consumer.py::TestConsumerIntegration::test_too_large_messages_getone`

```
>           result: Optional[TResult] = func()

/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/site-packages/_pytest/runner.py:341:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/site-packages/_pytest/runner.py:262: in <lambda>
    lambda: ihook(item=item, **kwds), when=when, reraise=reraise
/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/site-packages/pluggy/_hooks.py:493: in __call__
    return self._hookexec(self.name, self._hookimpls, kwargs, firstresult)
/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/site-packages/pluggy/_manager.py:115: in _hookexec
    return self._inner_hookexec(hook_name, methods, kwargs, firstresult)
/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/site-packages/_pytest/unraisableexception.py:93: in pytest_runtest_teardown
    yield from unraisable_exception_runtest_hook()
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

>               warnings.warn(pytest.PytestUnraisableExceptionWarning(msg))
E               pytest.PytestUnraisableExceptionWarning: Exception ignored in: <function StreamWriter.__del__ at 0x7f3d2f748a40>
E
E               Traceback (most recent call last):
E                 File "/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/asyncio/streams.py", line 397, in __del__
E                   self.close()
E                 File "/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/asyncio/streams.py", line 343, in close
E                   return self._transport.close()
E                          ^^^^^^^^^^^^^^^^^^^^^^^
E                 File "/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/asyncio/selector_events.py", line 1206, in close
E                   super().close()
E                 File "/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/asyncio/selector_events.py", line 871, in close
E                   self._loop.call_soon(self._call_connection_lost, None)
E                 File "/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/asyncio/base_events.py", line 772, in call_soon
E                   self._check_closed()
E                 File "/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/asyncio/base_events.py", line 519, in _check_closed
E                   raise RuntimeError('Event loop is closed')
E               RuntimeError: Event loop is closed

/opt/hostedtoolcache/Python/3.12.0/x64/lib/python3.12/site-packages/_pytest/unraisableexception.py:78: PytestUnraisableExceptionWarning
```

<hr/>

https://github.com/ods/aiokafka/actions/runs/7572567954/job/20622809790

`tests/test_consumer.py::TestConsumerIntegration::test_kip_345_disabled`

https://github.com/aio-libs/aiokafka/actions/runs/8269331444/job/22624480929

`tests/test_consumer.py::TestConsumerIntegration::test_kip_345_enabled`

```
Expected: mock({TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=0)})
  Actual: mock({TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=0), TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=1)})

pytest introspection follows:

Args:
assert ({TopicPartit...artition=1)},) == ({TopicPartit...artition=0)},)
  At index 0 diff: {TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=0), TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=1)} != {TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=0)}
  Full diff:
    (
  -  {TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=0)},,
  ?                                                                              - -
  +  {TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=0),
  +   TopicPartition(topic='topic-test_kip_345_disabled-FLbCSaVSPC', partition=1)},,
    )
```

<hr/>

https://github.com/aio-libs/aiokafka/actions/runs/9733268751/job/26860002493

Broker startup logs:
```
[2024-06-30 16:12:09,841] ERROR Exiting Kafka due to fatal exception (kafka.Kafka$)
java.lang.IllegalArgumentException: requirement failed: Each listener must have a different port, listeners: PLAINTEXT://:35127,SSL://:54847,SASL_PLAINTEXT://:46291,SASL_SSL://:35127
```
