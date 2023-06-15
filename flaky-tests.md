<hr/>

https://github.com/aio-libs/aiokafka/actions/runs/5136838735/jobs/9244123052

`tests/test_consumer.py::TestConsumerIntegration::test_max_poll_interval_ms`

```
        await listener1.assignment_ready.wait()
        await listener2.assignment_ready.wait()
>       self.assertTrue(consumer1.assignment())
E       AssertionError: set() is not true

tests/test_consumer.py:2024: AssertionError
```

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
