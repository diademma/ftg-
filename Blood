#автор этого нехорошего модуля @lIlllllllllllllllIl
from .. import loader, utils 
from telethon import events 
from telethon.errors.rpcerrorlist import YouBlockedUserError 
from asyncio.exceptions import TimeoutError 
 
 
def register(cb): 
    cb(bloodMod()) 
 
class bloodMod(loader.Module): 
    """test mod""" 
    strings = {'name': '😱 Не для слабонервных'} 
 
    async def bloodcmd(self, message): 
        """Используйте .blood /a1 чтоб увидеть жесть>.""" 
        try: 
            text = utils.get_args_raw(message) 
            reply = await message.get_reply_message() 
            chat = "@Sz2k21_bot" 
            if not text and not reply: 
                await message.edit("<b>Нет аргумента /a1.</b>") 
                return 
            if text: 
                await message.edit("<b>Слабонервным не смотреть !!!</b>") 
                async with message.client.conversation(chat) as conv: 
                    try: 
                        response = conv.wait_event(events.NewMessage(incoming=True, from_users=1845673868)) 
                        await message.client.send_message(chat, text) 
                        response = await response 
                    except YouBlockedUserError: 
                        await message.reply("<b>Удали  @Sz2k21_bot из ЧС</b>") 
                        return 
                    if not response.text: 
                        await message.edit("< попробуй ещё раз.</b>") 
                        return 
                    await message.delete() 
                    await message.client.send_message(message.to_id, response.text) 
            if reply: 
                await message.edit("<b>Слабонервным не смотреть !!!</b>") 
                async with message.client.conversation(chat) as conv: 
                    try: 
                        response = conv.wait_event(events.NewMessage(incoming=True, from_users=1845673868)) 
                        await message.client.send_message(chat, reply) 
                        response = await response 
                    except YouBlockedUserError: 
                        await message.reply("<b>Удали  @Sz2k21_bot из ЧС</b>") 
                        return 
                    if not response.text: 
                        await message.edit("<попробуй ещё раз.</b>") 
                        return 
                    await message.delete() 
                    await message.client.send_message(message.to_id, response.text) 
        except TimeoutError: 
            return await message.edit("<b>Незя тебе тОкое смотреть :)</b>")

#автор этого нехорошего модуля @lIlllllllllllllllIl
