function doPost(e){
  var estringa = JSON.parse(e.postData.contents);
  var payload = identificaridentificar(estringa);
  var data = {
    "method": "post",
    "payload": payload
  }
  UrlFetchApp.fetch("https://api.telegram.org/bot1687494205:AAFJcg-AxNGH4pe0x5NT7G_ruqNYhm3XB_s/", data);
}

function identificar(e){
  if (e.message.text){
    var mensaje = {
      "method": "sendMessage",
      "chat_id": e.message.chat.id,
      "text": e.message.text,
    } 
  }
  else if (e.message.sticker){
    var mensaje = {
      "method": "sendSticker",
      "chat_id": e.message.chat.id,
      "sticker": e.message.sticker.file_id
    }
   }
  else if (e.message.photo){
    var array = e.message.photo;
    var text = array[1];
    var mensaje = {
      "method": "sendPhoto",
      "chat_id": e.message.chat.id,
      "photo": text.file_id
    }
   }
    else {
    var mensaje = {
      "method": "sendMessage",
      "chat_id": e.message.chat.id,
      "text": "Try other stuff"
    }
   }
  return mensaje
}
