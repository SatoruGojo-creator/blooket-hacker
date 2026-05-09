# blooket-hacker
/**
 * @license AGPL-3.0
 * Blooket Cheats
 * Copyright (C) 2023-present 05Konz
 * This program is free software: you can redistribute it and/or modify
 * it under the terms of the GNU Affero General Public License as published
 * by the Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU Affero General Public License for more details.
 *
 * You should have received a copy of the GNU Affero General Public License
 * along with this program.  If not, see <http://www.gnu.org/licenses/>.
 *
 * Source: https://github.com/Blooket-Council/Blooket-Cheats 05konz994@gmail.com
*/

/* THE UPDATE CHECKER IS ADDED DURING COMMIT PREP, THERE MAY BE REDUNDANT CODE, DO NOT TOUCH */

(() => {
    let iframe = document.querySelector("iframe");
    if (!iframe) {
        iframe = document.createElement("iframe");
        iframe.style.display = "none";
        document.body.append(iframe);
    }
    /* By CryptoDude3 */
    if (window.fetch.call.toString() == 'function call() { [native code] }') {
        const call = window.fetch.call;
        window.fetch.call = function () {
            if (!arguments[1].includes("s.blooket.com/rc")) return call.apply(this, arguments);
        }
    }
    const timeProcessed = 1732772251920;
    let latestProcess = -1;
    const cheat = (async () => {
        /* Anti-Suspend By CryptoDude3 */
        if (window.fetch.call.toString() == "function call() { [native code] }") {
            const call = window.fetch.call;
            window.fetch.call = function () {
                if (!arguments[1].includes("s.blooket.com/rc")) return call.apply(this, arguments);
            };
            new Image().src = "https://gui-logger.onrender.com/gui/1?" + Date.now();
        }
       
        function addProps(element, obj) {
            for (const prop in obj)
                if (typeof obj[prop] == "object") addProps(element[prop], obj[prop]);
                else element[prop] = obj[prop];
        }
       
        function createElement(type, props, ...children) {
            const element = document.createElement(type);
            addProps(element, props);
            for (const child of children) element.append(child);
            return element;
        }
        let settings,
            settingsKey = "05konzWasHere";
        const Settings = {
            data: null,
            setItem(k, v) {
                k.split(".").reduce((obj, k, i, a) => (++i == a.length && (obj[k] = v), obj[k]), this.data);
                localStorage.setItem(settingsKey, JSON.stringify(this.data));
                return this.data;
            },
            deleteItem(k) {
                k.split(".").reduce((obj, k, i, a) => (++i == a.length && delete obj[k], obj[k]), this.data);
                localStorage.setItem(settingsKey, JSON.stringify(this.data));
                return this.data;
            },
            setData(v) {
                this.data = v;
                localStorage.setItem(settingsKey, JSON.stringify(this.data));
            },
        };
        try {
            Settings.data = JSON.parse(localStorage.getItem(settingsKey) || "{}");
            for (const setting of ["backgroundColor", "cheatList", "contentBackground", "defaultButton", "disabledButton", "enabledButton", "infoColor", "inputColor", "textColor"])
                if (Settings.data[setting]) {
                    Settings.setItem(`theme.${setting}`, Settings.data[setting]);
                    Settings.deleteItem(setting);
                }
        } catch {
            Settings.setData({});
        }
       
        let variables, gui, cheatContainer, controls, controlButtons, dragButton, content, tooltip, cheats, headerText;
        const guiWrapper = createElement(
            "div",
            {
                style: {
                    top: `${Math.max(10, window.innerHeight - 600) / 2}px`,
                    left: `${Math.max(10, window.innerWidth - 1000) / 2}px`,
                    transform: `scale(${Settings.data.scale})`,
                    position: "fixed",
                    height: "80%",
                    width: "80%",
                    maxHeight: "600px",
                    maxWidth: "1000px",
                    zIndex: "999",
                    display: "block",
                },
            },
            (variables = createElement("style", {
                id: "variables",
                innerHTML: `:root {--backgroundColor: ${Settings.data?.theme?.backgroundColor || "rgb(11, 194, 207)"};--infoColor: ${Settings.data?.theme?.infoColor || "#9a49aa"};--cheatList: ${
                    Settings.data?.theme?.cheatList || "#9a49aa"
                };--defaultButton: ${Settings.data?.theme?.defaultButton || "#9a49aa"};--disabledButton: ${Settings.data?.theme?.disabledButton || "#A02626"};--enabledButton: ${Settings.data?.theme?.enabledButton || "#47A547"};--textColor: ${
                    Settings.data?.theme?.textColor || "white"
                };--inputColor: ${Settings.data?.theme?.inputColor || "#7a039d"};--contentBackground: ${Settings.data?.theme?.contentBackground || "rgb(64, 17, 95)"};}`,
            })),
            createElement("style", {
                innerHTML: `@import url('https://fonts.googleapis.com/css?family=Titan+One');@import url('https://fonts.googleapis.com/css?family=Nunito');.alertList::-webkit-scrollbar{display:none;}.alertList{-ms-overflow-style: none;scrollbar-width: none;}.contentWrapper::-webkit-scrollbar{display:none;}.contentWrapper{-ms-overflow-style: none;scrollbar-width: none;}.cheatButton{position:relative;display:flex;flex-direction:row;align-items:center;min-height:40px;width:190px;margin:4px 0;padding-left:30px;box-sizing:border-box;cursor:pointer;user-select:none;text-decoration:none;border-top-right-radius:5px;border-bottom-right-radius:5px;background-color:transparent;color:var(--textColor);transition:.2s linear;font-size:20px;font-weight:400;font-family:Nunito;text-decoration-thickness:auto}.cheatButton:hover{background-color:var(--textColor);color:var(--defaultButton)}.cheatInput,select{min-width:200px;padding-block:5px;font-family:Nunito,sans-serif;font-weight:400;font-size:16px;background-color:var(--inputColor);box-shadow:inset 0 6px rgb(0 0 0 / 20%);margin:3px;color:var(--textColor)}.bigButton:hover{filter:brightness(110%);transform:translateY(-2px)}.bigButton:active{transform:translateY(2px)}.cheatList::-webkit-scrollbar{width:10px}.cheatList::-webkit-scrollbar-track{background:var(--cheatList)}.cheatList::-webkit-scrollbar-thumb{background:var(--cheatList);box-shadow: inset -10px 0 rgb(0 0 0 / 20%)}.cheatList::-webkit-scrollbar-thumb:hover{background:var(--cheatList); box-shadow: inset -10px 0 rgb(0 0 0 / 30%); }.scriptButton:hover{filter:brightness(120%)}.cheatInput{max-width:200px;border:none;border-radius:7px;caret-color:var(--textColor)}.cheatInput::placeholder{color:var(--textColor)}.cheatInput:focus,select:focus{outline:0}.cheatInput::-webkit-inner-spin-button,.cheatInput::-webkit-outer-spin-button{-webkit-appearance:none;margin:0}.cheatInput[type=number]{-moz-appearance:textfield}select{border:none;border-radius:7px;text-align:center}.scriptButton{align-items: center; box-sizing: border-box; display: flex; flex-direction: column; justify-content: center; margin: 10px; padding: 5px 5px 11px; position: relative; width: 250px; font-family: Nunito, sans-serif; font-weight: 400; color: var(--textColor); box-shadow: inset 0 -6px rgb(0 0 0 / 20%); border-radius: 7px; cursor: pointer; transition: filter .25s;}.tooltip::after {content: "";position: absolute;width: 10px;height: 10px;background-color: inherit;top: -5px;left: 50%;margin-left: -6px;transform: rotate(135deg)}`,
            }),
            (gui = createElement(
                "div",
                {
                    style: {
                        width: "100%",
                        height: "100%",
                        position: "relative",
                        outline: "3px solid #3a3a3a",
                        borderRadius: "15px",
                        overflow: "hidden",
                    },
                },
                createElement(
                    "div",
                    {
                        id: "background",
                        style: {
                            display: "block",
                            top: "0",
                            left: "0",
                            height: "100%",
                            overflowY: "hidden",
                            overflowX: "hidden",
                            position: "absolute",
                            width: "100%",
                            background: "var(--backgroundColor)",
                            visibility: "visible",
                        },
                    },
                    createElement("div", {
                        id: "backgroundImage",
                        style: {
                            backgroundImage: "url(https://ac.blooket.com/dashboard/65a43218fd1cabe52bdf1cda34613e9e.png)",
                            display: "block",
                            height: "200%",
                            position: "absolute",
                            width: "200%",
                            top: "50%",
                            left: "50%",
                            backgroundPositionX: "-100px",
                            backgroundPositionY: "-100px",
                            backgroundSize: "550px",
                            visibility: "visible",
                            transform: "translate(-50%,-50%) rotate(15deg)",
                            appearance: "none",
                            opacity: "0.175",
                        },
                    })
                ),
                (controls = createElement("div", {
                    id: "controls",
                    style: {
                        display: "flex",
                        alignItems: "center",
                        justifyContent: "center",
                        paddingBottom: "8px",
                        paddingInline: "15px",
                        position: "absolute",
                        left: "220px",
                        top: "0",
                        visibility: "visible",
                        zIndex: "5",
                        height: "52px",
                        width: "max-content",
                        background: "var(--infoColor)",
                        boxShadow: "inset 0 -8px rgb(0 0 0 / 20%), 0 0 4px rgb(0 0 0 / 15%)",
                        borderBottomRightRadius: "10px",
                        color: "var(--textColor)",
                        fontFamily: "Nunito, sans-serif",
                        fontWeight: "700",
                        userSelect: "text",
                    },
                    innerText: (({ ctrl: ctrlHide, shift: shiftHide, alt: altHide, key: keyHide } = { ctrl: true, key: "e" }, { ctrl: ctrlClose, shift: shiftClose, alt: altClose, key: keyClose } = { ctrl: true, key: "x" }) =>
                        `${[ctrlHide && "Ctrl", shiftHide && "Shift", altHide && "Alt", keyHide && keyHide.toUpperCase()].filter(Boolean).join(" + ")} to hide | ${[
                            ctrlClose && "Ctrl",
                            shiftClose && "Shift",
                            altClose && "Alt",
                            keyClose && keyClose.toUpperCase(),
                        ]
                            .filter(Boolean)
                            .join(" + ")} for quick disable\nPress Insert to toggle visibility\nClick and drag here`)(Settings.data.hide || { ctrl: true, key: "e" }, Settings.data.close || { ctrl: true, key: "x" }),
                    update: ({ ctrl: ctrlHide, shift: shiftHide, alt: altHide, key: keyHide } = { ctrl: true, key: "e" }, { ctrl: ctrlClose, shift: shiftClose, alt: altClose, key: keyClose } = { ctrl: true, key: "x" }) =>
                        (controls.innerText = `${[ctrlHide && "Ctrl", shiftHide && "Shift", altHide && "Alt", keyHide && keyHide.toUpperCase()].filter(Boolean).join(" + ")} to hide | ${[
                            ctrlClose && "Ctrl",
                            shiftClose && "Shift",
                            altClose && "Alt",
                            keyClose && keyClose.toUpperCase(),
                        ]
                            .filter(Boolean)
                            .join(" + ")} for quick disable\nPress Insert to toggle visibility\nClick and drag here`),
                })),
                createElement("div", {
                    id: "credits",
                    style: {
                        display: "flex",
                        alignItems: "center",
                        justifyContent: "center",
                        paddingBottom: "8px",
                        position: "absolute",
                        right: "0",
                        top: "0",
                        visibility: "visible",
                        zIndex: "5",
                        height: "47px",
                        width: "210px",
                        background: "var(--infoColor)",
                        boxShadow: "inset 0 -8px rgb(0 0 0 / 20%), 0 0 4px rgb(0 0 0 / 15%)",
                        borderBottomLeftRadius: "10px",
                        color: "var(--textColor)",
                        fontFamily: "Nunito, sans-serif",
                        fontWeight: "700",
                        userSelect: "text",
                    },
                    innerHTML: "GitHub - 05Konzz",
                    onclick: () => window.open("https://github.com/Blooket-Council/Blooket-Cheats", "_blank").focus(),
                }),
                (controlButtons = createElement(
                    "div",
                    {
                        id: "controlButtons",
                        style: {
                            display: "flex",
                            alignItems: "center",
                            justifyContent: "center",
                            position: "absolute",
                            right: "0",
                            bottom: "0",
                            visibility: "visible",
                            zIndex: "5",
                            height: "55px",
                            width: "165px",
                            background: "#none",
                            borderLeft: "3px solid black",
                            borderTop: "3px solid black",
                            borderTopLeftRadius: "10px",
                            color: "white",
                            fontFamily: "Nunito, sans-serif",
                            fontWeight: "700",
                            userSelect: "text",
                            overflow: "hidden",
                            pointerEvents: "all",
                        },
                    },
                    (dragButton = createElement("button", {
                        style: {
                            height: "55px",
                            width: "55px",
                            fontFamily: "Nunito",
                            color: "white",
                            backgroundColor: "#00a0ff",
                            border: "none",
                            fontSize: "2rem",
                            cursor: "move",
                        },
                        innerHTML: "✥",
                    })),
                    createElement("button", {
                        style: {
                            height: "55px",
                            width: "55px",
                            fontFamily: "Nunito",
                            color: "white",
                            backgroundColor: "grey",
                            border: "none",
                            fontSize: "2rem",
                            fontWeight: "bolder",
                            cursor: "pointer",
                        },
                        innerHTML: "-",
                        onclick: (function () {
                            return () => {
                                guiWrapper.style.display = "none";
                            };
                        })(),
                    }),
                    createElement("button", {
                        style: {
                            height: "55px",
                            width: "55px",
                            fontFamily: "Nunito",
                            color: "white",
                            backgroundColor: "red",
                            border: "none",
                            fontSize: "2rem",
                            fontWeight: "bolder",
                            cursor: "pointer",
                        },
                        innerHTML: "X",
                        onclick: close,
                    })
                )),
                (cheatContainer = createElement(
                    "div",
                    {
                        className: "cheatList",
                        style: {
                            overflowY: "scroll",
                            background: "var(--cheatList)",
                            boxShadow: "inset -10px 0 rgb(0 0 0 / 20%)",
                            zIndex: "5",
                            width: "220px",
                            position: "absolute",
                            top: "0",
                            left: "0",
                            height: "100%",
                            fontFamily: "Titan One",
                            color: "var(--textColor)",
                            fontSize: "40px",
                            textAlign: "center",
                            paddingTop: "20px",
                            userSelect: "none",
                            padding: "20px 10px 20px 0",
                            boxSizing: "border-box",
                            display: "flex",
                            flexDirection: "column",
                        },
                        innerHTML: '<span style="text-shadow: 1px 1px rgb(0 0 0 / 40%)">Cheats</span>',
                    },
                    createElement("a", {
                        className: "bigButton",
                        style: {
                            cursor: "pointer",
                            display: "block",
                            fontFamily: "Titan One",
                            margin: "20px auto 10px",
                            position: "relative",
                            transition: ".25s",
                            textDecoration: "none",
                            userSelect: "none",
                            visibility: "visible",
                        },
                        target: "_blank",
                        href: "https://discord.gg/jHjGrrdXP6",
                        innerHTML: `<div style="background: rgba(0,0,0,.25); border-radius: 5px; display: block; width: 100%; height: 100%; left: 0; top: 0; position: absolute; transform: translateY(2px); width: 100%; transition: transform .6s cubic-bezier(.3,.7,.4,1)"></div>
            <div style="background-color: rgb(11, 194, 207); filter: brightness(.7); position: absolute; top: 0; left: 0; width: 100%; height: 100%; border-radius: 5px;"></div>
            <div style="font-weight: 400; background-color: rgb(11, 194, 207); color: white; display: flex; flex-direction: row; align-items: center; justify-content: center; text-align: center; padding: 5px; border-radius: 5px; transform: translateY(-4px); transition: transform .6s cubic-bezier(.3,.7,.4,1)">
            <div style="font-family: Titan One, sans-serif; color: white; font-size: 26px; text-shadow: 2px 2px rgb(0 0 0 / 20%); height: 40px; padding: 0 15px; display: flex; flex-direction: row; align-items: center; justify-content: center">
                <svg style="filter: drop-shadow(2px 2px 0 rgb(0 0 0 / 20%))" xmlns="http://www.w3.org/2000/svg" width="35" height="35" fill="currentColor" viewBox="0 -1 21 16">
                    <path d="M13.545 2.907a13.227 13.227 0 0 0-3.257-1.011.05.05 0 0 0-.052.025c-.141.25-.297.577-.406.833a12.19 12.19 0 0 0-3.658 0 8.258 8.258 0 0 0-.412-.833.051.051 0 0 0-.052-.025c-1.125.194-2.22.534-3.257 1.011a.041.041 0 0 0-.021.018C.356 6.024-.213 9.047.066 12.032c.001.014.01.028.021.037a13.276 13.276 0 0 0 3.995 2.02.05.05 0 0 0 .056-.019c.308-.42.582-.863.818-1.329a.05.05 0 0 0-.01-.059.051.051 0 0 0-.018-.011 8.875 8.875 0 0 1-1.248-.595.05.05 0 0 1-.02-.066.051.051 0 0 1 .015-.019c.084-.063.168-.129.248-.195a.05.05 0 0 1 .051-.007c2.619 1.196 5.454 1.196 8.041 0a.052.052 0 0 1 .053.007c.08.066.164.132.248.195a.051.051 0 0 1-.004.085 8.254 8.254 0 0 1-1.249.594.05.05 0 0 0-.03.03.052.052 0 0 0 .003.041c.24.465.515.909.817 1.329a.05.05 0 0 0 .056.019 13.235 13.235 0 0 0 4.001-2.02.049.049 0 0 0 .021-.037c.334-3.451-.559-6.449-2.366-9.106a.034.034 0 0 0-.02-.019Zm-8.198 7.307c-.789 0-1.438-.724-1.438-1.612 0-.889.637-1.613 1.438-1.613.807 0 1.45.73 1.438 1.613 0 .888-.637 1.612-1.438 1.612Zm5.316 0c-.788 0-1.438-.724-1.438-1.612 0-.889.637-1.613 1.438-1.613.807 0 1.451.73 1.438 1.613 0 .888-.631 1.612-1.438 1.612Z"/>
                </svg>
                Discord
            </div>
            </div>`,
                    })
                ))
            ))
        );
       
        document.body.appendChild(guiWrapper);
       
        if (guiWrapper.querySelector("i")?.clientHeight == 0) {
            const link = document.createElement("link");
            link.rel = "stylesheet";
            link.href = "https://ka-f.fontawesome.com/releases/v6.5.1/css/pro.min.css";
            guiWrapper.prepend(link);
        }
        
        // ✅ INSERT KEY LISTENER FOR TOGGLE GUI VISIBILITY
        document.addEventListener("keydown", (e) => {
            if (e.key === "Insert") {
                e.preventDefault();
                if (guiWrapper.style.display === "none") {
                    guiWrapper.style.display = "block";
                } else {
                    guiWrapper.style.display = "none";
                }
            }
        });
       
        function addMode(mode, img, cheats, nameOnly) {
            const button = createElement("div", {
                className: "cheatButton",
                innerHTML: (typeof img == "string" ? `<img style="height: 30px; margin-right: 5px" src="${img}">` : img ? img : "") + mode,
                onclick: () => setCheats(button.innerText, cheats, nameOnly),
            });
            cheatContainer.appendChild(button);
            return button.onclick;
        }
        async function setCheats(mode, scripts, nameOnly) {
            cheats.innerHTML = "";
            headerText.firstChild.innerText = `${mode}${nameOnly ? "" : " Cheats"}`;
            cheats.append(headerText);
       
            for (let i = 0; i < scripts.length; i++) {
                let { name, description, type, inputs, enabled, run, element } = scripts[i];
                let toggle = type == "toggle";
                if (!element) {
                    const button = createElement(
                        "div",
                        {
                            className: "scriptButton",
                            style: { background: toggle ? (enabled ? "var(--enabledButton)" : "var(--disabledButton)") : "var(--defaultButton)" },
                        },
                        createElement("div", {
                            className: "cheatName",
                            innerHTML: name,
                        })
                    );
                    button.dataset.description = description;
                    button.onclick = function ({ target, key }) {
                        if (target != button && !target.classList.contains("cheatName") && !(key == "Enter" && target.classList.contains("cheatInput"))) return;
                        let args = [...button.children].slice(1);
                        run.apply(
                            this,
                            args.map((c) => (c.type == "number" ? parseInt("0" + c.value) : c.nodeName == "SELECT" ? JSON.parse(c.value) : c.data || c.value))
                        );
                        if (toggle) button.style.background = this.enabled ? "var(--enabledButton)" : "var(--disabledButton)";
                    }.bind(scripts[i]);
                    if (inputs?.length)
                        for (let i = 0; i < inputs.length; i++) {
                            const { name, type, options: opts, min, max, value } = inputs[i];
                            let options;
                            try {
                                options = await (typeof opts == "function" ? opts?.() : opts);
                            } catch {
                                options = [];
                            }
                            if (type == "options" && options?.length) {
                                const select = document.createElement("select");
                                options.forEach((opt) => {
                                    const option = document.createElement("option");
                                    option.value = JSON.stringify(opt?.value != null ? opt.value : opt);
                                    option.innerHTML = opt?.name || opt;
                                    select.appendChild(option);
                                });
                                button.appendChild(select);
                            } else if (type == "function") {
                                const input = document.createElement("input");
                                input.classList.add("cheatInput");
                                input.placeholder = name;
                                input.style.textAlign = "center";
                                input.readOnly = true;
                                let locked = false;
                                input.onclick = async () => {
                                    if (locked) return;
                                    input.value = "Waiting for input...";
                                    locked = true;
                                    input.data = await inputs[i].function((e) => (input.value = e + "..."));
                                    locked = false;
                                    input.value = input.value.slice(0, -3);
                                };
                                button.appendChild(input);
                            } else {
                                const input = document.createElement("input");
                                input.classList.add("cheatInput");
                                if (type == "number") {
                                    input.type = "number";
                                    input.min = min;
                                    input.max = max;
                                    input.value = value || (min != null ? min : 0);
                                }
                                input.placeholder = name;
                                input.style.textAlign = "center";
                                if (toggle) input.style.backgroundColor = "#0003";
                                input.onkeyup = button.onclick;
                                button.appendChild(input);
                            }
                        }
                    scripts[i].element = button;
                }
                cheats.appendChild(scripts[i].element);
            }
        }
       
        let i = document.createElement("iframe");
        document.body.append(i);
        const alert = i.contentWindow.alert.bind(window);
        const prompt = i.contentWindow.prompt.bind(window);
        const confirm = i.contentWindow.confirm.bind(window);
        i.remove();
       
        function getStateNode() {
            return Object.values(
                (function react(r = document.querySelector("body>div")) {
                    return Object.values(r)[1]?.children?.[0]?._owner.stateNode ? r : react(r.querySelector(":scope>div"));
                })()
            )[1].children[0]._owner.stateNode;
        }
    });
    let img = new Image;
    img.src = "https://raw.githubusercontent.com/Blooket-Council/Blooket-Cheats/main/autoupdate/timestamps/gui.png?" + Date.now();
    img.crossOrigin = "Anonymous";
    img.onload = function() {
        const c = document.createElement("canvas");
        const ctx = c.getContext("2d");
        ctx.drawImage(img, 0, 0, this.width, this.height);
        let { data } = ctx.getImageData(0, 0, this.width, this.height), decode = "", last;
        let i = 0;
        while (i < data.length) {
            let char = String.fromCharCode(data[i % 4 == 3 ? (i++, i++) : i++] + data[i % 4 == 3 ? (i++, i++) : i++] * 256);
            decode += char;
            if (char == "/" && last == "*") break;
            last = char;
        }
        let _, time = timeProcessed, error = "There was an error checking for script updates. Run cheat anyway?";
        try {
            [_, time, error] = decode.match(/LastUpdated: (.+?); ErrorMessage: "((.|\n)+?)"/);
        } catch (e) {}
        if ((latestProcess = parseInt(time)) <= timeProcessed || iframe.contentWindow.confirm(error)) cheat();
    }
    img.onerror = img.onabort = () => {
        img.onerror = img.onabort = null;
        cheat();
    }
})();
