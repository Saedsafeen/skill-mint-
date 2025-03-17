# skill-mint-import React, { useState } from 'react';
import { View, Text, TextInput, TouchableOpacity, StyleSheet, Image } from 'react-native';

const App = () => {
  const [emailOrPhone, setEmailOrPhone] = useState('');
  const [password, setPassword] = useState('');
  const [isLogin, setIsLogin] = useState(true);

  // اسم التطبيق: "SkillMint" مع شعار ورقة نعناع 🍃
  const Logo = () => (
    <View style={styles.logoContainer}>
      <Text style={styles.logoText}>🍃 SkillMint</Text>
      <Text style={styles.slogan}>Learn a Skill in 60 Seconds</Text>
    </View>
  );

  return (
    <View style={styles.container}>
      <Logo />
      
      {/* إما تسجيل دخول أو إنشاء حساب */}
      {isLogin ? (
        <Text style={styles.title}>تسجيل الدخول</Text>
      ) : (
        <Text style={styles.title}>إنشاء حساب</Text>
      )}

      {/* حقل الإيميل/الهاتف */}
      <TextInput
        style={styles.input}
        placeholder="البريد الإلكتروني أو رقم الهاتف"
        placeholderTextColor="#666"
        value={emailOrPhone}
        onChangeText={setEmailOrPhone}
      />

      {/* حقل كلمة المرور */}
      <TextInput
        style={styles.input}
        placeholder="كلمة المرور"
        placeholderTextColor="#666"
        secureTextEntry
        value={password}
        onChangeText={setPassword}
      />

      {/* زر الإجراء الرئيسي */}
      <TouchableOpacity style={styles.button}>
        <Text style={styles.buttonText}>{isLogin ? 'دخول' : 'إنشاء حساب'}</Text>
      </TouchableOpacity>

      {/* التبديل بين الشاشتين */}
      <TouchableOpacity onPress={() => setIsLogin(!isLogin)}>
        <Text style={styles.switchText}>
          {isLogin ? 'ليس لديك حساب؟ أنشئ واحدًا' : 'لديك حساب؟ سجل دخول'}
        </Text>
      </TouchableOpacity>
    </View>
  );
};

// الألوان: أسود (خلفية) ، أحمر (أزرار) ، أبيض (نصوص)
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#000',
    padding: 20,
    justifyContent: 'center',
  },
  logoContainer: {
    alignItems: 'center',
    marginBottom: 40,
  },
  logoText: {
    color: '#fff',
    fontSize: 32,
    fontWeight: 'bold',
  },
  slogan: {
    color: '#666',
    fontSize: 16,
    marginTop: 8,
  },
  title: {
    color: '#fff',
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 20,
    textAlign: 'center',
  },
  input: {
    backgroundColor: '#1a1a1a',
    color: '#fff',
    padding: 15,
    borderRadius: 10,
    marginBottom: 15,
  },
  button: {
    backgroundColor: '#ff0000',
    padding: 15,
    borderRadius: 10,
    alignItems: 'center',
    marginTop: 10,
  },
  buttonText: {
    color: '#fff',
    fontWeight: 'bold',
    fontSize: 16,
  },
  switchText: {
    color: '#ff0000',
    textAlign: 'center',
    marginTop: 20,
  },
});

export default App;
