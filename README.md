// Aplicación de mensajería personalizada para BerMatModZ import React, { useState, useEffect } from 'react'; import { Button } from '@/components/ui/button'; import { Card, CardContent } from '@/components/ui/card'; import { Input } from '@/components/ui/input'; import { motion } from 'framer-motion'; import { ChevronRight, User, MessageSquare, Settings, PhoneCall, LogOut } from 'lucide-react';

const BerMatModZApp = () => { const [user, setUser] = useState(''); const [password, setPassword] = useState(''); const [loggedIn, setLoggedIn] = useState(false); const [chatList, setChatList] = useState([ { name: 'Proyecto BerMat_Bot', message: 'Hola, ¿cuándo sale la próxima actualización?', time: '12:35 PM' }, { name: 'Anonymous Team', message: 'Estamos listos para la misión.', time: '11:20 AM' }, { name: 'FAMA (Fuerza Anónima de Mentes Avanzadas)', message: 'Tenemos nuevos códigos listos.', time: '10:45 AM' }, { name: 'Cliente - Bot', message: 'Hermano, quiero un bot personalizado.', time: '9:30 AM' }, { name: 'Briyidth Jhorgina', message: 'Te amo muchísimo, mi rey.', time: '8:15 AM' }, ]);

const handleLogin = () => { if (user && password) setLoggedIn(true); };

const handleLogout = () => { setLoggedIn(false); setUser(''); setPassword(''); };

return ( <div className="bg-black min-h-screen p-8 text-white"> <div className="text-center mb-8"> <motion.h1 initial={{ opacity: 0, y: -50 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 1.2 }} className="text-5xl font-bold text-emerald-400"> ⚡ BerMatModZ App 🔥 </motion.h1> <motion.p initial={{ opacity: 0, y: -20 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 1.2 }} className="text-xl text-red-300"> 𝑩𝑬𝑹𝑴𝑨𝑻𝑴𝑶𝑫𝑺 🫦 𝑻𝑬 𝑫𝑨 🤡𝑳𝑨 𝑩𝑰𝑬𝑵𝑽𝑬𝑵𝑰𝑫𝑨 👹 𝑨𝑳 🔪𝑴𝑼𝑵𝑫𝑶 𝑫𝑬 🔥𝑪𝑰𝑽𝑬𝑹𝑨𝑻𝑨𝑸𝑼𝑬 😎 𝒀 💥𝑪𝑰𝑽𝑬𝑹𝑺𝑬𝑮𝑼𝑹𝑰𝑫𝑨𝑫 👽🤖 </motion.p> </div>

{!loggedIn ? (
    <Card className="mx-auto w-full max-w-md bg-gray-900 border border-gray-700 p-6 rounded-2xl shadow-lg">
      <CardContent>
        <Input type="text" placeholder="Nombre de usuario" value={user} onChange={(e) => setUser(e.target.value)} className="mb-4 bg-gray-800 text-white border-emerald-500" />
        <Input type="password" placeholder="Contraseña" value={password} onChange={(e) => setPassword(e.target.value)} className="mb-4 bg-gray-800 text-white border-emerald-500" />
        <Button onClick={handleLogin} className="w-full bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2 rounded-full">Iniciar Sesión</Button>
      </CardContent>
    </Card>
  ) : (
    <Card className="mx-auto w-full max-w-4xl bg-gray-900 border border-gray-700 p-6 rounded-2xl shadow-xl">
      <CardContent>
        <motion.h2 initial={{ opacity: 0, scale: 0.8 }} animate={{ opacity: 1, scale: 1 }} transition={{ duration: 1 }} className="text-4xl font-bold text-emerald-400 mb-6">
          Bienvenido, {user}!
        </motion.h2>
        <ul className="text-white mb-6">
          {chatList.map((chat, index) => (
            <li key={index} className="flex items-center justify-between py-2 border-b border-gray-700">
              <div>
                <p className="text-lg font-bold">{chat.name}</p>
                <p className="text-gray-400 text-sm">{chat.message}</p>
              </div>
              <span className="text-gray-500 text-sm">{chat.time}</span>
            </li>
          ))}
        </ul>
        <Button onClick={handleLogout} className="bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-4 rounded-lg flex items-center">
          <LogOut className="mr-2" /> Cerrar Sesión
        </Button>
      </CardContent>
    </Card>
  )}
</div>

); };

export default BerMatModZApp;

