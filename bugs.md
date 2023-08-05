<hr/>

`ResourceWarning` when `AIOKafkaConsumer` fails to connect.

```
  File "/user/service/app/kafka.py", line 19, in get_consumer
    async with AIOKafkaConsumer(
  File "/user/.local/lib/python3.10/site-packages/aiokafka/consumer/consumer.py", line 1271, in __aenter__
    await self.start()
  File "/user/.local/lib/python3.10/site-packages/aiokafka/consumer/consumer.py", line 351, in start
    await self._client.bootstrap()
  File "/user/.local/lib/python3.10/site-packages/aiokafka/client.py", line 251, in bootstrap
    raise KafkaConnectionError(
kafka.errors.KafkaConnectionError: KafkaConnectionError: Unable to bootstrap from [('kafka', 9092, <AddressFamily.AF_UNSPEC: 0>)]
```

```
Traceback (most recent call last):
  File "/user/.local/lib/python3.10/site-packages/aiokafka/consumer/consumer.py", line 331, in __del__
    _warnings.warn(f"Unclosed AIOKafkaConsumer {self!r}",
ResourceWarning: Unclosed AIOKafkaConsumer <aiokafka.consumer.consumer.AIOKafkaConsumer object at 0xffff97faf3a0>
```

<hr/>
