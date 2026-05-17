# ⚛️ Component Factory

Gerador de componentes React prontos para uso imediato.

## 📌 Sobre o Projeto

**Component Factory** é um script em Bash que gera 33 componentes React simples e reutilizáveis. Basta rodar o script, copiar a pasta `components` para seu projeto React e começar a usar.

Sem instalação. Sem configuração. Só copiar e colar.

---

## 📦 Componentes Incluídos

### Botões (10)
- ButtonPrimary - Botão primário
- ButtonSecondary - Botão secundário
- ButtonDanger - Botão de perigo
- ButtonSuccess - Botão de sucesso
- ButtonLarge - Botão grande
- ButtonSmall - Botão pequeno
- ButtonOutline - Botão com borda
- ButtonRounded - Botão arredondado
- ButtonDisabled - Botão desabilitado
- ButtonIcon - Botão com ícone

### Inputs (15)
- InputText - Campo de texto
- InputPassword - Campo de senha com mostrar/esconder
- InputEmail - Campo de e-mail
- InputNumber - Campo numérico
- InputTel - Campo de telefone
- InputDate - Seletor de data
- InputTime - Seletor de hora
- InputDateTime - Seletor de data e hora
- InputSearch - Campo de busca com lupa
- Textarea - Campo de texto multilinha
- Checkbox - Caixa de seleção
- Radio - Botão de opção
- Select - Menu suspenso
- InputRange - Slider
- InputColor - Seletor de cor

### Feedback (3)
- Alert - Alertas (success, error, warning, info)
- Badge - Tags (default, success, danger, warning)
- Spinner - Indicador de carregamento

### Layout (3)
- Card - Cartão com imagem, título e conteúdo
- Navbar - Barra de navegação
- Modal - Janela modal

### Dados (2)
- Table - Tabela de dados
- Toggle - Switch liga/desliga

**Total: 33 componentes**

---

## 🙏 Agradecimento

Ferramenta criada pra facilitar a vida de quem desenvolve com React.

Código aberto, feito no Brasil 🇧🇷

## 📜 Licença

Uso livre para fins educacionais e profissionais

```bash
#!/bin/bash

echo "=============================="
echo "   Component Factory"
echo "   Gerador de componentes React"
echo "=============================="

mkdir -p components

bottom(){

# 1 Botao Primario
cat << 'EOF' > components/ButtonPrimary.jsx
const ButtonPrimary = ({ children, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: '#3b82f6', color: 'white', padding: '8px 16px', border: 'none', borderRadius: '4px', cursor: 'pointer' }}>{children}</button>;
};
export default ButtonPrimary;
EOF

# 2 Botao Secundario
cat << 'EOF' > components/ButtonSecondary.jsx
const ButtonSecondary = ({ children, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: '#6b7280', color: 'white', padding: '8px 16px', border: 'none', borderRadius: '4px', cursor: 'pointer' }}>{children}</button>;
};
export default ButtonSecondary;
EOF

# 3 Botao Perigo
cat << 'EOF' > components/ButtonDanger.jsx
const ButtonDanger = ({ children, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: '#ef4444', color: 'white', padding: '8px 16px', border: 'none', borderRadius: '4px', cursor: 'pointer' }}>{children}</button>;
};
export default ButtonDanger;
EOF

# 4 Botao Sucesso
cat << 'EOF' > components/ButtonSuccess.jsx
const ButtonSuccess = ({ children, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: '#10b981', color: 'white', padding: '8px 16px', border: 'none', borderRadius: '4px', cursor: 'pointer' }}>{children}</button>;
};
export default ButtonSuccess;
EOF

# 5 Botao Grande
cat << 'EOF' > components/ButtonLarge.jsx
const ButtonLarge = ({ children, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: '#3b82f6', color: 'white', padding: '12px 24px', fontSize: '18px', border: 'none', borderRadius: '4px', cursor: 'pointer' }}>{children}</button>;
};
export default ButtonLarge;
EOF

# 6 Botao Pequeno
cat << 'EOF' > components/ButtonSmall.jsx
const ButtonSmall = ({ children, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: '#3b82f6', color: 'white', padding: '4px 8px', fontSize: '12px', border: 'none', borderRadius: '4px', cursor: 'pointer' }}>{children}</button>;
};
export default ButtonSmall;
EOF

# 7 Botao Outline
cat << 'EOF' > components/ButtonOutline.jsx
const ButtonOutline = ({ children, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: 'transparent', color: '#3b82f6', padding: '8px 16px', border: '2px solid #3b82f6', borderRadius: '4px', cursor: 'pointer' }}>{children}</button>;
};
export default ButtonOutline;
EOF

# 8 Botao Arredondado
cat << 'EOF' > components/ButtonRounded.jsx
const ButtonRounded = ({ children, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: '#3b82f6', color: 'white', padding: '8px 16px', border: 'none', borderRadius: '50px', cursor: 'pointer' }}>{children}</button>;
};
export default ButtonRounded;
EOF

# 9 Botao Desabilitado
cat << 'EOF' > components/ButtonDisabled.jsx
const ButtonDisabled = ({ children }) => {
    return <button disabled style={{ backgroundColor: '#9ca3af', color: 'white', padding: '8px 16px', border: 'none', borderRadius: '4px', cursor: 'not-allowed' }}>{children}</button>;
};
export default ButtonDisabled;
EOF

# 10 Botao com Icone
cat << 'EOF' > components/ButtonIcon.jsx
const ButtonIcon = ({ children, icon, onClick }) => {
    return <button onClick={onClick} style={{ backgroundColor: '#3b82f6', color: 'white', padding: '8px 16px', border: 'none', borderRadius: '4px', cursor: 'pointer' }}>{icon && <span style={{ marginRight: '8px' }}>{icon}</span>}{children}</button>;
};
export default ButtonIcon;
EOF
}

criar_index(){
    cat << 'EOF' > components/index.js
// Botoes
export { default as ButtonPrimary } from './ButtonPrimary';
export { default as ButtonSecondary } from './ButtonSecondary';
export { default as ButtonDanger } from './ButtonDanger';
export { default as ButtonSuccess } from './ButtonSuccess';
export { default as ButtonLarge } from './ButtonLarge';
export { default as ButtonSmall } from './ButtonSmall';
export { default as ButtonOutline } from './ButtonOutline';
export { default as ButtonRounded } from './ButtonRounded';
export { default as ButtonDisabled } from './ButtonDisabled';
export { default as ButtonIcon } from './ButtonIcon';

// Inputs
export { default as InputText } from './InputText';
export { default as InputPassword } from './InputPassword';
export { default as InputEmail } from './InputEmail';
export { default as InputNumber } from './InputNumber';
export { default as InputTel } from './InputTel';
export { default as InputDate } from './InputDate';
export { default as InputTime } from './InputTime';
export { default as InputDateTime } from './InputDateTime';
export { default as InputSearch } from './InputSearch';
export { default as Textarea } from './Textarea';
export { default as Checkbox } from './Checkbox';
export { default as Radio } from './Radio';
export { default as Select } from './Select';
export { default as InputRange } from './InputRange';
export { default as InputColor } from './InputColor';
export { default as Toggle } from './Toggle';

// Feedback
export { default as Alert } from './Alert';
export { default as Badge } from './Badge';
export { default as Spinner } from './Spinner';

// Layout
export { default as Card } from './Card';
export { default as Navbar } from './Navbar';
export { default as Modal } from './Modal';

// Dados
export { default as Table } from './Table';
EOF
}

input(){
    cat << 'EOF' > components/InputText.jsx
const InputText = ({ label, value, onChange, placeholder }) => {
    const styles = {
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <input type="text" value={value} onChange={onChange} placeholder={placeholder} style={styles.input} />
        </div>
    );
};
export default InputText;
EOF

    cat << 'EOF' > components/InputPassword.jsx
import { useState } from 'react';

const InputPassword = ({ label, value, onChange, placeholder }) => {
    const [show, setShow] = useState(false);
    
    const styles = {
        container: { display: 'flex', alignItems: 'center', gap: '8px' },
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', flex: 1 },
        button: { padding: '8px 12px', cursor: 'pointer', background: '#f3f4f6', border: '1px solid #ddd', borderRadius: '4px' }
    };
    
    return (
        <div>
            {label && <label>{label}</label>}
            <div style={styles.container}>
                <input 
                    type={show ? 'text' : 'password'} 
                    value={value} 
                    onChange={onChange} 
                    placeholder={placeholder} 
                    style={styles.input} 
                />
                <button onClick={() => setShow(!show)} style={styles.button}>
                    {show ? 'Ocultar' : 'Mostrar'}
                </button>
            </div>
        </div>
    );
};
export default InputPassword;
EOF

    cat << 'EOF' > components/InputEmail.jsx
const InputEmail = ({ label, value, onChange, placeholder }) => {
    const styles = {
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <input type="email" value={value} onChange={onChange} placeholder={placeholder || 'exemplo@email.com'} style={styles.input} />
        </div>
    );
};
export default InputEmail;
EOF

    cat << 'EOF' > components/InputNumber.jsx
const InputNumber = ({ label, value, onChange, placeholder, min, max }) => {
    const styles = {
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <input type="number" value={value} onChange={onChange} placeholder={placeholder} min={min} max={max} style={styles.input} />
        </div>
    );
};
export default InputNumber;
EOF

    cat << 'EOF' > components/InputTel.jsx
const InputTel = ({ label, value, onChange, placeholder }) => {
    const styles = {
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <input type="tel" value={value} onChange={onChange} placeholder={placeholder || '(00) 00000-0000'} style={styles.input} />
        </div>
    );
};
export default InputTel;
EOF

    cat << 'EOF' > components/InputDate.jsx
const InputDate = ({ label, value, onChange }) => {
    const styles = {
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <input type="date" value={value} onChange={onChange} style={styles.input} />
        </div>
    );
};
export default InputDate;
EOF

    cat << 'EOF' > components/InputTime.jsx
const InputTime = ({ label, value, onChange }) => {
    const styles = {
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <input type="time" value={value} onChange={onChange} style={styles.input} />
        </div>
    );
};
export default InputTime;
EOF

    cat << 'EOF' > components/InputDateTime.jsx
const InputDateTime = ({ label, value, onChange }) => {
    const styles = {
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <input type="datetime-local" value={value} onChange={onChange} style={styles.input} />
        </div>
    );
};
export default InputDateTime;
EOF

    cat << 'EOF' > components/InputSearch.jsx
const InputSearch = ({ value, onChange, placeholder }) => {
    const styles = {
        input: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%', paddingLeft: '32px' }
    };
    return (
        <div style={{ position: 'relative' }}>
            <span style={{ position: 'absolute', left: '8px', top: '50%', transform: 'translateY(-50%)' }}>🔍</span>
            <input type="search" value={value} onChange={onChange} placeholder={placeholder || 'Buscar...'} style={styles.input} />
        </div>
    );
};
export default InputSearch;
EOF

    cat << 'EOF' > components/Textarea.jsx
const Textarea = ({ label, value, onChange, placeholder, rows = 4 }) => {
    const styles = {
        textarea: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%', resize: 'vertical' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <textarea value={value} onChange={onChange} placeholder={placeholder} rows={rows} style={styles.textarea} />
        </div>
    );
};
export default Textarea;
EOF

    cat << 'EOF' > components/Checkbox.jsx
const Checkbox = ({ label, checked, onChange }) => {
    return (
        <label style={{ display: 'flex', alignItems: 'center', gap: '8px', cursor: 'pointer' }}>
            <input type="checkbox" checked={checked} onChange={onChange} />
            <span>{label}</span>
        </label>
    );
};
export default Checkbox;
EOF

    cat << 'EOF' > components/Radio.jsx
const Radio = ({ name, label, value, selectedValue, onChange }) => {
    return (
        <label style={{ display: 'flex', alignItems: 'center', gap: '8px', cursor: 'pointer' }}>
            <input type="radio" name={name} value={value} checked={selectedValue === value} onChange={onChange} />
            <span>{label}</span>
        </label>
    );
};
export default Radio;
EOF

    cat << 'EOF' > components/Select.jsx
const Select = ({ label, options, value, onChange }) => {
    const styles = {
        select: { padding: '8px 12px', border: '1px solid #ddd', borderRadius: '4px', width: '100%' }
    };
    return (
        <div>
            {label && <label>{label}</label>}
            <select value={value} onChange={onChange} style={styles.select}>
                {options.map((opt, idx) => (
                    <option key={idx} value={opt.value}>{opt.label}</option>
                ))}
            </select>
        </div>
    );
};
export default Select;
EOF

    cat << 'EOF' > components/InputRange.jsx
const InputRange = ({ label, value, onChange, min = 0, max = 100 }) => {
    return (
        <div>
            {label && <label>{label} ({value})</label>}
            <input type="range" value={value} onChange={onChange} min={min} max={max} style={{ width: '100%' }} />
        </div>
    );
};
export default InputRange;
EOF

    cat << 'EOF' > components/InputColor.jsx
const InputColor = ({ label, value, onChange }) => {
    return (
        <div>
            {label && <label>{label}</label>}
            <div style={{ display: 'flex', alignItems: 'center', gap: '8px' }}>
                <input type="color" value={value} onChange={onChange} style={{ width: '50px', height: '40px', cursor: 'pointer' }} />
                <span>{value}</span>
            </div>
        </div>
    );
};
export default InputColor;
EOF
}

alert(){
    cat << 'EOF' > components/Alert.jsx
const Alert = ({ type, children }) => {
    const styles = {
        success: { backgroundColor: '#d1fae5', color: '#065f46', padding: '12px', borderRadius: '4px' },
        error: { backgroundColor: '#fee2e2', color: '#991b1b', padding: '12px', borderRadius: '4px' },
        warning: { backgroundColor: '#fed7aa', color: '#92400e', padding: '12px', borderRadius: '4px' },
        info: { backgroundColor: '#dbeafe', color: '#1e40af', padding: '12px', borderRadius: '4px' }
    };
    return <div style={styles[type]}>{children}</div>;
};
export default Alert;
EOF
}

Badge(){
    cat << 'EOF' > components/Badge.jsx
const Badge = ({ children, variant = 'default' }) => {
    const styles = {
        default: { backgroundColor: '#6b7280', color: 'white', padding: '4px 8px', borderRadius: '12px', fontSize: '12px' },
        success: { backgroundColor: '#10b981', color: 'white', padding: '4px 8px', borderRadius: '12px', fontSize: '12px' },
        danger: { backgroundColor: '#ef4444', color: 'white', padding: '4px 8px', borderRadius: '12px', fontSize: '12px' },
        warning: { backgroundColor: '#f59e0b', color: 'white', padding: '4px 8px', borderRadius: '12px', fontSize: '12px' }
    };
    return <span style={styles[variant]}>{children}</span>;
};
export default Badge;
EOF
}

Card(){
    cat << 'EOF' > components/Card.jsx
const Card = ({ title, children, image }) => {
    return (
        <div style={{ border: '1px solid #e5e7eb', borderRadius: '8px', overflow: 'hidden', maxWidth: '300px' }}>
            {image && <img src={image} style={{ width: '100%', height: 'auto' }} alt={title} />}
            <div style={{ padding: '16px' }}>
                <h3 style={{ margin: '0 0 8px 0' }}>{title}</h3>
                <div>{children}</div>
            </div>
        </div>
    );
};
export default Card;
EOF
}

Navbar(){
    cat << 'EOF' > components/Navbar.jsx
const Navbar = ({ logo, links }) => {
    return (
        <nav style={{ display: 'flex', justifyContent: 'space-between', padding: '16px', backgroundColor: '#1f2937', color: 'white' }}>
            <div style={{ fontWeight: 'bold' }}>{logo}</div>
            <div style={{ display: 'flex', gap: '16px' }}>
                {links.map((link, index) => <a key={index} href={link.url} style={{ color: 'white', textDecoration: 'none' }}>{link.label}</a>)}
            </div>
        </nav>
    );
};
export default Navbar;
EOF
}

modal(){
    cat << 'EOF' > components/Modal.jsx
const Modal = ({ isOpen, onClose, title, children }) => {
    if (!isOpen) return null;
    return (
        <div style={{ position: 'fixed', top: 0, left: 0, right: 0, bottom: 0, backgroundColor: 'rgba(0,0,0,0.5)', display: 'flex', justifyContent: 'center', alignItems: 'center' }}>
            <div style={{ backgroundColor: 'white', padding: '24px', borderRadius: '8px', minWidth: '300px' }}>
                <h3>{title}</h3>
                <div>{children}</div>
                <button onClick={onClose}>Fechar</button>
            </div>
        </div>
    );
};
export default Modal;
EOF
}

spinner(){
    cat << 'EOF' > components/Spinner.jsx
const Spinner = () => {
    const spinKeyframes = `
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    `;
    return (
        <div>
            <style>{spinKeyframes}</style>
            <div style={{ display: 'inline-block', width: '40px', height: '40px', border: '4px solid #f3f3f3', borderTop: '4px solid #3b82f6', borderRadius: '50%', animation: 'spin 1s linear infinite' }}></div>
        </div>
    );
};
export default Spinner;
EOF
}

table(){
    cat << 'EOF' > components/Table.jsx
const Table = ({ columns, data }) => {
    return (
        <table style={{ width: '100%', borderCollapse: 'collapse' }}>
            <thead>
                <tr>
                    {columns.map((col, idx) => <th key={idx} style={{ borderBottom: '2px solid #ddd', padding: '8px', textAlign: 'left' }}>{col}</th>)}
                </tr>
            </thead>
            <tbody>
                {data.map((row, idx) => (
                    <tr key={idx}>
                        {columns.map((col, colIdx) => <td key={colIdx} style={{ borderBottom: '1px solid #ddd', padding: '8px' }}>{row[col.toLowerCase()]}</td>)}
                    </tr>
                ))}
            </tbody>
        </table>
    );
};
export default Table;
EOF
}

toggle(){
    cat << 'EOF' > components/Toggle.jsx
const Toggle = ({ checked, onChange }) => {
    return (
        <button onClick={onChange} style={{ backgroundColor: checked ? '#3b82f6' : '#9ca3af', width: '50px', height: '24px', borderRadius: '12px', border: 'none', cursor: 'pointer', position: 'relative' }}>
            <span style={{ display: 'block', width: '20px', height: '20px', backgroundColor: 'white', borderRadius: '50%', position: 'absolute', top: '2px', left: checked ? '28px' : '2px', transition: 'left 0.2s' }}></span>
        </button>
    );
};
export default Toggle;
EOF
}

# Chama todas as funcoes
bottom
input
alert
Badge
Card
Navbar
modal
spinner
table
toggle
criar_index

```
