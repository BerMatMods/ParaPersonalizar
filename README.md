// WhatsApp Web Modificado para BerMatModZ import React, { useState, useEffect } from 'react'; import { motion } from 'framer-motion'; import { Home, User, Star, LogOut, MessageSquare, Settings, PhoneCall, Code, Heart, Globe, ShieldAlert, Cpu, Activity } from 'lucide-react';

const BerMatModZWhatsAppWeb = () => { const [user, setUser] = useState('Anth'Zz Berrocal'); const [chatList, setChatList] = useState([ { name: '⚡ BerMat-Bot MD 🔥', message: '¡Listo para revolucionar WhatsApp!', time: '12:35 PM' }, { name: 'BerMat_Mods', message: 'Desarrollando nuevas herramientas avanzadas.', time: '11:20 AM' }, { name: 'FAMA', message: 'Código listo para hackear el sistema.', time: '10:45 AM' }, { name: 'Cliente - Bot', message: 'Hermano, quiero un bot personalizado.', time: '9:30 AM' }, { name: 'Briyidth Jhorgina', message: 'Te amo muchísimo, mi rey.', time: '8:15 AM' }, { name: 'Anth'Zz Berrocal', message: 'Vamos a conquistar el mundo tecnológico.', time: '7:00 AM' }, ]); const [currentChat, setCurrentChat] = useState(null); const [messages, setMessages] = useState([]);

const selectChat = (chat) => { setCurrentChat(chat); setMessages([ { sender: chat.name, message: 'Hola, ¿cómo estás?', time: '12:00 PM' }, { sender: user, message: '¡Todo bien! ¿Y tú?', time: '12:05 PM' }, ]); };

const sendMessage = (e) => { e.preventDefault(); const message = e.target.message.value; if (message) { setMessages([...messages, { sender: user, message, time: new Date().toLocaleTimeString() }]); e.target.reset(); } };

return ( <div className="bg-black min-h-screen p-8 text-white"> <motion.div initial={{ opacity: 0, y: -100 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 1 }} className="bg-gradient-to-r from-emerald-600 via-purple-600 to-red-600 p-6 rounded-2xl shadow-lg text-center mb-8"> <h1 className="text-6xl font-bold text-white drop-shadow-lg">⚡ BerMatModZ Web 🔥</h1> <p className="text-xl text-white mt-4"> 𝑩𝑬𝑹𝑴𝑨𝑻𝑴𝑶𝑫𝑺 🫦 𝑻𝑬 𝑫𝑨 🤡𝑳𝑨 𝑩𝑰𝑬𝑵𝑽𝑬𝑵𝑰𝑫𝑨 👹 𝑨𝑳 🔪𝑴𝑼𝑵𝑫𝑶 𝑫𝑬 🔥𝑪𝑰𝑽𝑬𝑹𝑨𝑻𝑨𝑸𝑼𝑬 😎 𝒀 💥𝑪𝑰𝑽𝑬𝑹𝑺𝑬𝑮𝑼𝑹𝑰𝑫𝑨𝑫 👽🤖 </p> <p className="text-lg text-white mt-2"> Creador: Anth'Zz Berrocal<br /> Alias: BerMatModZ<br /> Proyectos: ⚡BerMat-Bot MD🔥, BerMat_Mods, FAMA (Fuerza Anónima de Mentes Avanzadas)<br /> Ubicación: Andahuaylas<br /> Pasión: Tecnología y Hacking Profesional<br /> </p> </motion.div>

<div className="flex gap-6">
    <div className="w-1/4 bg-gray-900 p-4 rounded-2xl">
      <h2 className="text-2xl font-bold mb-4">Chats</h2>
      <ul>
        {chatList.map((chat, index) => (
          <li key={index} className="mb-4 cursor-pointer hover:bg-gray-800 p-3 rounded-lg" onClick={() => selectChat(chat)}>
            <strong>{chat.name}</strong>
            <p className="text-gray-400">{chat.message}</p>
          </li>
        ))}
      </ul>
    </div>
    <div className="flex-1 bg-gray-900 p-6 rounded-2xl">
      {currentChat ? (
        <>
          <h2 className="text-2xl font-bold mb-4">{currentChat.name}</h2>
          <ul className="mb-4">
            {messages.map((msg, index) => (
              <li key={index} className="mb-2">
                <strong className="text-emerald-400">{msg.sender}:</strong> <span className="text-gray-300">{msg.message}</span> <span className="text-gray-500 text-sm">({msg.time})</span>
              </li>
            ))}
          </ul>
          <form onSubmit={sendMessage}>
            <input name="message" placeholder="Escribe tu mensaje..." className="w-full p-3 mb-4 bg-gray-800 text-white border-emerald-500 rounded-lg" />
            <button type="submit" className="w-full bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2 rounded-full">Enviar</button>
          </form>
        </>
      ) : (
        <p className="text-gray-500">Selecciona un chat para empezar a conversar.</p>
      )}
    </div>
  </div>
</div>

); };

export default BerMatModZWhatsAppWeb;

