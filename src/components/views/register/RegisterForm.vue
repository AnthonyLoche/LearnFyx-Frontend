<template>
  <div class="form-container">
    <div class="form-wrapper">
      <div class="form-header">
        <h2 class="form-title">Criar Conta</h2>
        <p class="form-subtitle">Preencha os dados abaixo para começar sua jornada.</p>
      </div>

      <form @submit.prevent="handleSubmit" class="form">
        <div class="form-group">
          <label for="name" class="label">Nome Completo</label>
          <div class="input-wrapper">
            <span class="input-icon">
                <Account />
            </span>
            <input
              id="name"
              v-model="formData.name"
              type="text"
              placeholder="João Silva"
              class="input"
              required
            />
          </div>
        </div>

        <div class="form-group">
          <label for="email" class="label">Email</label>
          <div class="input-wrapper">
            <span class="input-icon">
                <Email />
            </span>
            <input
              id="email"
              v-model="formData.email"
              type="email"
              placeholder="seu@email.com"
              class="input"
              required
            />
          </div>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label for="phone" class="label">Telefone</label>
            <div class="input-wrapper">
              <span class="input-icon">
                <Phone />
              </span>
              <input
                id="phone"
                v-model="formData.phone"
                type="tel"
                placeholder="(11) 99999-9999"
                class="input"
                required
              />
            </div>
          </div>

          <div class="form-group">
            <label for="profession" class="label">Profissão</label>
            <div class="input-wrapper">
              <span class="input-icon">
                <Briefcase />
              </span>
              <input
                id="profession"
                v-model="formData.profession"
                type="text"
                placeholder="Desenvolvedor"
                class="input"
                required
              />
            </div>
          </div>
        </div>

        <div class="form-group">
          <label for="goal" class="label">Objetivo Principal</label>
          <div class="input-wrapper">
            <span class="input-icon">
                <Target />
            </span>
            <select
              id="goal"
              v-model="formData.goal"
              class="select"
              required
            >
              <option value="" disabled>Selecione seu objetivo</option>
              <option value="carreira">Mudar de carreira</option>
              <option value="habilidades">Desenvolver novas habilidades</option>
              <option value="promocao">Buscar promoção</option>
              <option value="empreender">Empreender</option>
              <option value="atualizar">Atualizar conhecimentos</option>
              <option value="hobby">Aprender por hobby</option>
            </select>
          </div>
        </div>

        <div class="form-group">
          <label for="password" class="label">Senha</label>
          <div class="input-wrapper">
            <span class="input-icon">
                <Lock />
            </span>
            <input
              id="password"
              v-model="formData.password"
              :type="showPassword ? 'text' : 'password'"
              placeholder="Mínimo 8 caracteres"
              class="input"
              required
              minlength="8"
            />
            <button
              type="button"
              @click="showPassword = !showPassword"
              class="toggle-password"
            >
              {{ showPassword ? '👁️' : '👁️‍🗨️' }}
            </button>
          </div>
          <div class="password-strength">
            <div class="strength-bar" :class="passwordStrength"></div>
          </div>
        </div>

        <div class="form-group">
          <label class="checkbox-wrapper terms-wrapper">
            <input 
              type="checkbox" 
              v-model="formData.agreeTerms"
              required
            />
            <span class="checkbox-label">
              Eu concordo com os 
              <a href="#" class="link">Termos de Uso</a> e 
              <a href="#" class="link">Política de Privacidade</a>
            </span>
          </label>
        </div>

        <button type="submit" class="submit-btn" :disabled="!formData.agreeTerms">
          Criar Minha Conta
          <span class="arrow"><ChevronRight /></span>
        </button>
      </form>

      <div class="divider">
        <span>OU CADASTRE-SE COM</span>
      </div>

      <div class="social-buttons">
        <button type="button" class="social-btn google" @click="registerWithGoogle">
          <svg viewBox="0 0 24 24" width="20" height="20">
            <path fill="#4285F4" d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"/>
            <path fill="#34A853" d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"/>
            <path fill="#FBBC05" d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l2.85-2.22.81-.62z"/>
            <path fill="#EA4335" d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z"/>
          </svg>
          Google
        </button>
        
        <button type="button" class="social-btn facebook" @click="registerWithFacebook">
          <svg viewBox="0 0 24 24" width="20" height="20" fill="#1877F2">
            <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
          </svg>
          Facebook
        </button>
      </div>

      <p class="login-link">
        Já tem uma conta? 
        <a href="#" class="link-primary">Faça login</a>
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import Account from 'vue-material-design-icons/Account.vue';
import Email from 'vue-material-design-icons/Email.vue';
import Phone from 'vue-material-design-icons/Phone.vue';
import Lock from 'vue-material-design-icons/Lock.vue';
import Briefcase from 'vue-material-design-icons/Briefcase.vue';
import Target from 'vue-material-design-icons/Target.vue';
import ChevronRight from 'vue-material-design-icons/ChevronRight.vue';

const showPassword = ref(false);

const formData = ref({
  name: '',
  email: '',
  phone: '',
  profession: '',
  goal: '',
  password: '',
  agreeTerms: false
});

const passwordStrength = computed(() => {
  const pwd = formData.value.password;
  if (pwd.length === 0) return '';
  if (pwd.length < 6) return 'weak';
  if (pwd.length < 10) return 'medium';
  return 'strong';
});

const handleSubmit = () => {
  console.log('Cadastro:', formData.value);
  alert('Cadastro realizado com sucesso!');
};

const registerWithGoogle = () => {
  console.log('Cadastro com Google');
  alert('Cadastro com Google');
};

const registerWithFacebook = () => {
  console.log('Cadastro com Facebook');
  alert('Cadastro com Facebook');
};
</script>

<style scoped>
.form-container {
  background-color: #f5f5f5;
  height: auto;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.form-wrapper {
  border-radius: 12px;
  padding: 3rem;
  width: 80%;
}

.form-header {
  margin-bottom: 2rem;
}

.form-title {
  font-size: 2rem;
  font-weight: 900;
  color: #1f2937;
  margin-bottom: 0.5rem;
}

.form-subtitle {
  color: #6b7280;
  font-size: 0.938rem;
}

span{
    display: flex;
    align-items: center;
    justify-content: center;
}

.form-subtitle {
  color: #64748b;
  font-size: 0.938rem;
}

.form {
  margin-bottom: 1.5rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.form-group {
  margin-bottom: 1.5rem;
}

.label {
  display: block;
  font-size: 0.875rem;
  font-weight: 600;
  color: #334155;
  margin-bottom: 0.5rem;
}

.input-wrapper {
  position: relative;
  display: flex;
  align-items: center;
}

.input-icon {
  position: absolute;
  left: 1rem;
  color: #64748b;
  font-size: 1.125rem;
  display: flex;
  align-items: center;
}

.input,
.select {
  width: 100%;
  padding: 0.875rem 1rem 0.875rem 3rem;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  font-size: 0.938rem;
  transition: all 0.3s;
  outline: none;
  background-color: white;
  color: #334155;
}

.input:focus,
.select:focus {
  border-color: #1e40af;
  box-shadow: 0 0 0 3px rgba(30, 64, 175, 0.1);
}

.select {
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg width='12' height='8' viewBox='0 0 12 8' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1 1.5L6 6.5L11 1.5' stroke='%2364748B' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 1rem center;
  padding-right: 3rem;
}

.toggle-password {
  position: absolute;
  right: 1rem;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 1.125rem;
  opacity: 0.6;
  transition: opacity 0.3s;
}

.toggle-password:hover {
  opacity: 1;
}

.password-strength {
  margin-top: 0.5rem;
  height: 4px;
  background-color: #e2e8f0;
  border-radius: 2px;
  overflow: hidden;
}

.strength-bar {
  height: 100%;
  transition: all 0.3s;
  border-radius: 2px;
}

.strength-bar.weak {
  width: 33%;
  background-color: #ef4444;
}

.strength-bar.medium {
  width: 66%;
  background-color: #f59e0b;
}

.strength-bar.strong {
  width: 100%;
  background-color: #059669;
}

.checkbox-wrapper {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  cursor: pointer;
}

.checkbox-wrapper input[type="checkbox"] {
  width: 20px;
  height: 20px;
  cursor: pointer;
  margin-top: 2px;
  flex-shrink: 0;
  accent-color: #1e40af;
}

.checkbox-label {
  font-size: 0.875rem;
  color: #64748b;
  line-height: 1.5;
  display: flex;
  flex-wrap: wrap;
  gap: 0.25rem;
}

.terms-wrapper {
  align-items: flex-start;
}

.link {
  color: #1e40af;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s;
}

.link:hover {
  color: #1e3a8a;
  text-decoration: underline;
}

.submit-btn {
  width: 100%;
  padding: 1rem;
  background-color: #0d7ff2;
  color: white;
  border: none;
  border-radius: 10px;
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  box-shadow: 0 4px 15px rgba(30, 64, 175, 0.3);
}

.submit-btn:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(30, 64, 175, 0.4);
}

.submit-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
  transform: none;
  box-shadow: none;
}

.arrow {
  font-size: 1.25rem;
  transition: transform 0.3s;
  display: flex;
  align-items: center;
}

.submit-btn:hover:not(:disabled) .arrow {
  transform: translateX(4px);
}

.divider {
  text-align: center;
  margin: 2rem 0;
  position: relative;
}

.divider::before,
.divider::after {
  content: '';
  position: absolute;
  top: 50%;
  width: 38%;
  height: 1px;
  background-color: #e2e8f0;
}

.divider::before {
  left: 0;
}

.divider::after {
  right: 0;
}

.divider span {
  padding: 0 1rem;
  color: #94a3b8;
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.5px;
}

.social-buttons {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 2rem;
}

.social-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  padding: 0.875rem 1rem;
  border: 1.5px solid #e2e8f0;
  border-radius: 10px;
  background-color: white;
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
  color: #334155;
}

.social-btn:hover {
  background-color: #f8fafc;
  border-color: #cbd5e1;
  transform: translateY(-1px);
}

.social-btn.google {
  color: #334155;
}

.social-btn.facebook {
  color: #1877F2;
}

.login-link {
  text-align: center;
  font-size: 0.875rem;
  color: #64748b;
  margin-top: 1rem;
}

.link-primary {
  color: #1e40af;
  text-decoration: none;
  font-weight: 700;
  transition: all 0.3s;
  margin-left: 0.25rem;
}

.link-primary:hover {
  color: #1e3a8a;
  text-decoration: underline;
}

@media (max-width: 768px) {
  .form-container {
    padding: 1rem;
  }
  
  .form-wrapper {
    padding: 2rem 1.5rem;
    width: 95%;
  }

  .form-title {
    font-size: 1.75rem;
  }

  .form-row {
    grid-template-columns: 1fr;
  }

  .social-buttons {
    grid-template-columns: 1fr;
  }
}
</style>