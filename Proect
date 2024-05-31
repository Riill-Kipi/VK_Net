using System;
using VkNet;
using VkNet.Model;
using VkNet.Enums.Filters;
using VkNet.Enums.SafetyEnums;
using VkNet.Categories;
using System.Threading.Tasks;
using System.Threading;
using VkNet.Enums.StringEnums;
using VkNet.Exception;
using System.Linq;
using System.Runtime.Remoting.Messaging;

namespace VkBot_DiplomNew_
{
    class Program
    {
        public static VkApi vk = new VkApi();
        static void Main(string[] args)
        {
            Console.WriteLine("Connect Bot");
            vk.Authorize(new VkNet.Model.ApiAuthParams
            {
                AccessToken = ""
            });
            while (true)
            {
                Thread.Sleep(50);
                Receive();
            }
        }

        public static bool Receive()
        {
            object[] minfo = GetMessage();
            long? userid = Convert.ToInt32(minfo[2]);
            if (minfo[0] == null)
            {
                return false;
            }
            string code = !string.IsNullOrEmpty(minfo[1].ToString()) ? minfo[1].ToString() : minfo[0].ToString();

            switch (code.ToLower())
            {
                case "1":
                    SendMessage("Тут случайный текст 1", userid, null);
                    break;
                case "2":
                    SendMessage("Тут случайный текст 2", userid, null);
                    break;
                case "3":
                    SendMessage("Тут случайный текст 3", userid, null);
                    break;
                case "4":
                    SendMessage("Тут случайный текст 4", userid, null);
                    break;
                case "5":
                    SendMessage("Тут случайный текст 5", userid, null);
                    break;
                case "6":
                    SendMessage("Тут случайный текст 6", userid, null);
                    break;
                case "7":
                    SendMessage("Тут случайный текст 7", userid, null);
                    break;
                case "8":
                    SendMessage("Тут случайный текст 8", userid, null);
                    break;
                case "9":
                    SendMessage("Тут случайный текст 9", userid, null);
                    break;
                case "10":
                    SendMessage("Тут случайный текст 10", userid, null);
                    break;
                default:
                    SendMessage("Здравствуйте, я бот-помощник. На данный момент я еще в разработке.", userid, null);
                    break;
            }
            return true;
        }

        public static void SendMessage(string message, long? userid, MessageKeyboard keyboard)
        {
            vk.Messages.Send(new MessagesSendParams
            {
                Message = message,
                PeerId = userid,
                RandomId = new Random().Next(),
                Keyboard = keyboard
            });
        }

        public static object[] GetMessage()
        {
            string message = "";
            string keyname = "";
            long? userid = 0;
            var messages = vk.Messages.GetDialogs(new MessagesDialogsGetParams
            {
                Count = 10,
                Unread = true
            });

            if (messages.Messages.Count != 0)
            {
                if (!string.IsNullOrEmpty(messages.Messages[0].Text))
                {
                    message = messages.Messages[0].Text.ToString();
                }
                else
                {
                    message = "";
                }
                if (messages.Messages[0].Payload != null)
                {
                    keyname = messages.Messages[0].Payload.ToString();
                }
                else
                {
                    keyname = "";
                }
                userid = messages.Messages[0].UserId.Value;
                object[] keys = new object[3] { message, keyname, userid };
                vk.Messages.MarkAsRead(userid.ToString());
                return keys;
            }
            else
            {
                return new object[] { null, null, null };
            }
        }
    }
}
