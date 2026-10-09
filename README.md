# 123456
针对中小学英语教学辅助教师提供帮助提升学习效率的智能体



@echo off
chcp 65001 >nul
title ZhiYan - Classroom English Speaking Agent

set "ROOT=%~dp0"
if "%ROOT:~-1%"=="\" set "ROOT=%ROOT:~0,-1%"
set "BACKEND=%ROOT%\prototype\backend"

echo ============================================================
echo    ZhiYan / English Speaking Classroom Agent
echo ============================================================
echo.
echo    Starting... please wait about 3 seconds.
echo.
echo    Your browser will open automatically.
echo    If it does not, open Chrome / Edge and go to:
echo.
echo        http://127.0.0.1:8000
echo.
echo    IMPORTANT: keep this window open while using it.
echo    To stop the service, just close this window.
echo.
echo ============================================================
echo.

set "PY=C:\Users\FLY\.workbuddy\binaries\python\versions\3.13.12\python.exe"
if not exist "%PY%" set "PY=python"

start "" cmd /c "timeout /t 3 >nul & start "" http://127.0.0.1:8000"

cd /d "%BACKEND%"
if errorlevel 1 (
  echo ERROR: cannot enter folder:
  echo   %BACKEND%
  echo Please check the folder still exists.
  pause
  exit /b 1
)

"%PY%" -m app.main --port 8000

echo.
echo ------------------------------------------------------------
echo    Service stopped.
echo    If there were red error lines above, screenshot this window.
echo ------------------------------------------------------------
pause
