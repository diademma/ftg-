from .. import loader, utils 
from telethon import events 
from telethon.errors.rpcerrorlist import YouBlockedUserError 
from asyncio.exceptions import TimeoutError 
 
 
def register(cb): 
    cb(WikiMod()) 
 
class WikiMod(loader.Module): 
    """Модуль для поиска инфы в Википедии """ 
    strings = {'name': 'Wikipedia_tio'} 
 
    async def wikicmd(self, message): 
        """Пиши .wiki + слово, можно реплай.""" 
        try: 
            text = utils.get_args_raw(message) 
            reply = await message.get_reply_message() 
            chat = "@just_zhenya_bot" 
            if not text and not reply: 
                await message.edit("<b>А эм... а что искать то...</b>") 
                return 
            if text: 
                await message.edit("<b>Ищу материал</b>") 
                async with message.client.conversation(chat) as conv: 
                    try: 
                        response = conv.wait_event(events.NewMessage(incoming=True, from_users=528677877)) 
                        await message.client.send_message(chat, "/wiki " + text) 
                        response = await response 
                    except YouBlockedUserError: 
                        await message.reply("<b>Удали из ЧС: @just_zhenya_bot</b>") 
                        return 
                    if not response.text: 
                        await message.edit("<Ещё раз пробуй</b>") 
                        return 
                    await message.delete() 
                    await message.client.send_message(message.to_id, response.text) 
            if reply: 
                await message.edit("<b>Ищу материал...</b>") 
                async with message.client.conversation(chat) as conv: 
                    try: 
                        response = conv.wait_event(events.NewMessage(incoming=True, from_users=528677877)) 
                        await message.client.send_message(chat, reply) 
                        response = await response 
                    except YouBlockedUserError: 
                        await message.reply("<b>Удали из ЧС: @just_zhenya_bot</b>") 
                        return 
                    if not response.text: 
                        await message.edit("<Пробуй еще раз </b>") 
                        return 
                    await message.delete() 
                    await message.client.send_message(message.to_id, response.text) 
        except TimeoutError: 
            return await message.edit("<b>Ну тут как бэ ... наши полномочия всё... закончились</b>")
