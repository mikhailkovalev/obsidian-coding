```python
import dataclasses
import asyncio
import tochka_clients
from aiohttp import ClientResponse


@dataclasses.dataclass
class SomeBinary(tochka_clients.BinaryClientBase):
    base_url: str = 'https://httpbin.org'

    @staticmethod
    async def handle_response_binary(response: ClientResponse) -> bytes:
        return await super().handle_response_binary(response)


async def run():
    api = SomeBinary()
    print(await api.get('/image'))


if __name__ == '__main__':
    asyncio.get_event_loop().run_until_complete(run())
```